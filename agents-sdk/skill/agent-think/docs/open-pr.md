# Autonomous PR Creation Guide (open-pr)

This guide documents the autonomous Pull Request workflow implemented by the `agent-think` PR agent. It details how the agent investigates a reported issue on `cloudflare/agents`, formulates a minimal fix, runs tests and checks, deploys a live temporary verification demo, pushes a fix branch, and submits a linked Pull Request.

---

## 1. Overview & Execution Context

### Purpose
The `open-pr` skill is triggered by an `@agent-think` invocation (or automated dispatch) on a GitHub issue. It takes the issue description, existing repro findings (if available), and any user instructions to one-shot create a fully tested, verified PR.

### Execution Context & Credentials
- **Identity**: Authored as `agent-think[bot]` (the GitHub App). Does not impersonate human users.
- **Backend Execution**: All `gh`, `git`, `npm`, `pnpm`, `curl`, and `wrangler` commands must run on the `container` backend (`bash({ command, backend: "container" })`). The `shell` backend lacks network access and necessary tool binaries.
- **Directories**:
  - Main workspace: `/workspace/agents`
  - Scratch demo/build areas: `/workspace/demo-<issueNumber>`
  - Container-local temp logs: `/temp` (outside the workspace mount, preventing session timeouts from large terminal outputs).

### Liveness Reaction
When the triggering message contains `trigger-comment-id`, immediately add a rocket reaction to signal activity:
```bash
gh api repos/<repository>/issues/comments/<trigger-comment-id>/reactions \
  -f content=rocket
```

---

## 2. Phase 1: Repository Setup & Issue Assessment

### Step 1: Clone Repository
Clone the repository directly under `/workspace`:
```bash
REPO_DIR="/workspace/$(basename <repo>)"
if [ ! -d "$REPO_DIR/.git" ]; then
  git clone https://github.com/<repo>.git "$REPO_DIR"
fi
cd "$REPO_DIR"
```

### Step 2: Gather All Context
Fetch the complete issue metadata, body, and all comments:
```bash
gh issue view <issueNumber> --repo <repo> --json title,body,labels,author,comments
```

**Key Information to Inspect**:
- **Repro Agent Comment**: Look for comments from prior `@agent-think repro` runs. These often contain:
  - Minimal reproduction code.
  - Live reproduction URL.
  - Observed vs. expected behaviors.
  - Root-cause hypothesis citing specific files and line numbers.
- **User Instructions**: Specific constraints, preferred fixes, or hints provided in the trigger comment.

### Step 3: Feasibility & Scope Decision
Assess whether the issue is solvable in a single autonomous shot:
- **Skip Conditions**:
  - Feature requests requiring architectural design.
  - Overly vague descriptions without clear repro steps.
  - Wide-ranging refactors spanning multiple disconnected subsystems.
  - Unclear or unverifiable root causes.
- **Skip Action**: Return `prOpened: false`, `skipped: true`, and post a polite comment explaining the reason and what additional info is required (prefixed with `Requested by @<requestedBy>`).

---

## 3. Phase 2: Root Cause Analysis & Branch Setup

### Step 1: Confirm the Root Cause
Read the relevant implementation files in `packages/agents`, `packages/think`, etc., confirming the hypothesis and identifying the smallest change needed.

### Step 2: Branch & Git Identity
Configure the bot's git identity and create a timestamped fix branch:
```bash
git config user.name "agent-think[bot]"
git config user.email "agent-think[bot]@users.noreply.github.com"
BRANCH="fix/issue-<issueNumber>-$(date +%s)"
git checkout -b "$BRANCH"
```

---

## 4. Phase 3: Implementing the Fix

### Principles for the Code Change
1. **Minimal Correct Change**: Touch the fewest files possible and maintain existing code styling and conventions.
2. **Regression Testing**: Add or update unit/integration tests that fail prior to the fix and pass after.
3. **Changesets**: For user-facing fixes in repos using Changesets, add a markdown file under `.changeset/`.
4. **Documentation & Examples**: If the fix modifies public APIs or behaviors demonstrated in `examples/*` or `docs/`, update them in the same PR.

---

## 5. Phase 4: Verification & Monorepo Checks

The monorepo uses `pnpm` + `Nx`. To prevent large terminal outputs from disconnecting the agent session, all noisy commands must redirect stdout/stderr to `/temp`:

```bash
mkdir -p /temp

# Install dependencies cleanly
CI=1 pnpm install --frozen-lockfile --reporter=append-only \
  > /temp/install.log 2>&1 || (tail -40 /temp/install.log; false)
tail -20 /temp/install.log

# Code formatting and linting
pnpm -w exec oxfmt --check . || pnpm -w exec oxfmt --write .
pnpm -w exec oxlint . || true

# Run targeted package typecheck and tests
pnpm --filter <package> typecheck > /temp/typecheck.log 2>&1; tail -30 /temp/typecheck.log
pnpm --filter <package> test > /temp/test.log 2>&1; tail -40 /temp/test.log
```

> [!IMPORTANT]
> Never open a PR whose own new tests fail. If test failures are unrelated or known flakiness, explicitly document them in the PR body.

---

## 6. Phase 5: Building & Deploying a Live Demo

Reviewers can verify the fix visually via a live temporary deployment.

### Step 1: Pack the Fixed Package
Build the fixed package and generate a `.tgz` tarball:
```bash
pnpm --filter <package> build
(cd packages/<package> && npm pack --pack-destination /workspace)
# Generates /workspace/<package>-x.y.z.tgz
```

### Step 2: Scaffold or Update the Demo
In `/workspace/demo-<issueNumber>`, use the 7-file minimal Vite + React template (or checkout the existing `repro/issue-<issueNumber>` branch) and install the local tarball:
```bash
npm install /workspace/<package>-x.y.z.tgz
```

### Step 3: Deploy & Verify
```bash
npm run deploy      # runs: vite build && wrangler deploy --temporary
curl -sS -i "<demoUrl>/" | head -5
```
Capture the `https://...workers.dev` URL as `demoUrl`.

*(Note: If the change has no runtime impact, such as docs or types only, skip the demo and note "no runtime surface to demo" in the PR).*

---

## 7. Phase 6: Commit, Push, and PR Creation

### Step 1: Commit and Push
```bash
git status --short
git add -A
git commit -m "fix: <concise description> (#<issueNumber>)"
git push -u origin "$BRANCH"
```

### Step 2: Submit Pull Request
Prepare the PR body in `/temp/pr-body.md` and create the PR:
```bash
gh pr create --repo <repo> \
  --base main \
  --head "$BRANCH" \
  --title "fix: <concise description> (#<issueNumber>)" \
  --body-file /temp/pr-body.md
```

### Required PR Body Structure
The PR body must contain:
1. `Requested by @<requestedBy>` (using sanitized mention from the envelope).
2. `Closes #<issueNumber>` (enables auto-closing on merge).
3. **Problem Statement**: Root cause analysis citing exact files and lines.
4. **Summary of Changes**: Why this is the minimal and correct solution.
5. **Testing**: Tests added, commands executed, and test suite results.
6. **Demo URL**:
   > Demo URL (expires after 60 mins): `<demoUrl>`
   > *Instructions on how to test the fix in the demo UI.*
7. **Reproduction Link**: Reference to the repro agent's comment/branch.
8. **Footer**: `🤖 generated by the pr-agent — please review carefully`.

*(Do not post a separate issue comment announcing the PR; GitHub automatically links the PR via `Closes #<issueNumber>`.)*

---

## 8. Phase 7: Structured Return Output

The agent execution completes by returning a structured result:

```typescript
type OpenPrResult = {
  prOpened: boolean;
  skipped: boolean;
  summary: string;
  prUrl?: string;
  branch?: string;
  testsPassed?: boolean;
  demoUrl?: string;
};
```
