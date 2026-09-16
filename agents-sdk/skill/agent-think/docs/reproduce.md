# Autonomous Bug Reproduction Guide (reproduce)

This guide documents the autonomous bug reproduction workflow implemented by the `agent-think` repro agent. It details how the agent investigates a reported issue on `cloudflare/agents`, scaffolds a minimal end-to-end reproducible application with a frontend UI, deploys it to a temporary Cloudflare account, verifies the bug, publishes an orphan reproduction branch, and reports the findings on the GitHub issue.

---

## 1. Overview & Execution Context

### Purpose
The `reproduce` skill handles reported bugs by independently recreating the issue in an isolated Cloudflare Worker environment. This allows maintainers and automated fix agents to confirm the bug, observe live symptoms, and access a ready-to-run reproduction branch.

### Runtime Environment
- **Backend**: All `gh`, `git`, `npm`, `curl`, and `wrangler` commands must be executed on the `container` backend (`bash({ command, backend: "container" })`).
- **Directories**:
  - Reference clone: `/workspace/agents`
  - Scratch reproduction project: `/workspace/repro-<issueNumber>`
  - Temporary publishing workspace: `/workspace/repro-publish-<issueNumber>`
  - Container-local temp logs: `/temp` (avoids terminal buffer overflow).

### Liveness Reaction
If the triggering prompt contains `trigger-comment-id`, immediately add a rocket reaction:
```bash
gh api repos/<repository>/issues/comments/<trigger-comment-id>/reactions \
  -f content=rocket
```

---

## 2. Phase 1: Issue Analysis & Feasibility Check

### Step 1: Clone Reference Repository
Clone a shallow copy of the repository into `/workspace`:
```bash
REPO_DIR="/workspace/$(basename <repo>)"
if [ ! -d "$REPO_DIR/.git" ]; then
  git clone --depth=1 https://github.com/<repo>.git "$REPO_DIR"
fi
```

### Step 2: Extract Issue Details
Fetch issue data and comments:
```bash
gh issue view <issueNumber> --repo <repo> --json title,body,labels,comments
```

Extract the following:
1. **Observed Behavior**: The exact defect or erroneous response reported.
2. **Expected Behavior**: What the system should have done.
3. **Reproduction Steps**: Code snippets, specific versions, configuration settings, or error stack traces.

### Step 3: Feasibility Decision
- **Non-Reproducible Criteria**: Feature requests, general questions, docs-only questions, or issues lacking concrete runnable behavior.
- **Action**: Stop early with `skipped: true`, `reproduced: false`, and post a polite comment explaining why, beginning with `Requested by @<requestedBy>`.

---

## 3. Phase 2: Codebase Investigation

Navigate through `/workspace/agents` to inspect:
- Core implementation in `packages/agents`, `packages/think`, etc.
- Closest reference implementation under `examples/`.
- Ensure version compatibility matches what the reporter described.

---

## 4. Phase 3: Minimal 7-File Reproduction Architecture

Scaffold a clean, minimal project in `/workspace/repro-<issueNumber>`. Every reproduction **must include a minimal Vite + React frontend** so maintainers can click the live URL, trigger the bug via a button, and see expected vs. actual output on screen.

```bash
REPRO_DIR="/workspace/repro-<issueNumber>"
mkdir -p "$REPRO_DIR"
cd "$REPRO_DIR"
```

### Required File Structure (7 Files)

#### 1. `package.json`
Specifies required dependencies and build scripts:
```json
{
  "name": "repro-issue-<issueNumber>",
  "type": "module",
  "private": true,
  "scripts": {
    "start": "vite dev",
    "deploy": "vite build && wrangler deploy --temporary"
  },
  "dependencies": {
    "agents": "^0.16.2",
    "react": "^19.2.7",
    "react-dom": "^19.2.7"
  },
  "devDependencies": {
    "@cloudflare/vite-plugin": "^1.40.2",
    "@cloudflare/workers-types": "^4.20260612.1",
    "@types/node": "^25.9.3",
    "@types/react": "^19.2.17",
    "@types/react-dom": "^19.2.3",
    "@vitejs/plugin-react": "^6.0.2",
    "typescript": "^6.0.3",
    "vite": "^8.0.16",
    "wrangler": "^4.100.0"
  }
}
```

#### 2. `vite.config.ts`
Configures `@cloudflare/vite-plugin`.
*(Note: Include `agents()` from `"agents/vite"` first in the plugins array if the server uses `@callable()` decorators)*:
```ts
import { cloudflare } from "@cloudflare/vite-plugin";
import react from "@vitejs/plugin-react";
import { defineConfig } from "vite";

export default defineConfig({
  plugins: [react(), cloudflare()]
});
```

#### 3. `index.html`
Placed directly in the project root:
```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Repro Issue #<issueNumber></title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/client.tsx"></script>
  </body>
</html>
```

#### 4. `src/client.tsx`
Provides an interactive verification UI:
```tsx
import { useState } from "react";
import { createRoot } from "react-dom/client";
import { useAgent } from "agents/react";

function App() {
  const [log, setLog] = useState<string[]>([]);
  const add = (m: string) => setLog((l) => [...l, `${new Date().toISOString()} ${m}`]);

  const agent = useAgent({
    agent: "repro-agent",
    name: "demo",
    onOpen: () => add("WebSocket connected"),
    onClose: () => add("WebSocket closed"),
    onMessage: (e) => add(`recv: ${e.data}`)
  });

  return (
    <main style={{ fontFamily: "monospace", padding: 16 }}>
      <h1>Issue #<issueNumber>: <Title></h1>
      <p><strong>Expected:</strong> <ExpectedBehavior></p>
      <p><strong>Actual (Bug):</strong> <ObservedBug></p>
      <button onClick={async () => {
        add("Triggering bug...");
        // Example: agent.call("testMethod", [...]) or fetch(...)
      }}>
        Trigger Bug
      </button>
      <pre style={{ background: "#f4f4f4", padding: 8, marginTop: 12 }}>
        {log.join("\n")}
      </pre>
    </main>
  );
}

createRoot(document.getElementById("root")!).render(<App />);
```

#### 5. `src/server.ts`
The Cloudflare Worker and Durable Object Agent backend:
```ts
import { Agent, routeAgentRequest } from "agents";

type Env = {
  ReproAgent: DurableObjectNamespace<ReproAgent>;
};

export class ReproAgent extends Agent<Env> {
  // Methods to reproduce the issue (e.g., onRequest, onConnect, onMessage, @callable)
}

export default {
  async fetch(request: Request, env: Env) {
    return (
      (await routeAgentRequest(request, env)) ||
      new Response("Not found", { status: 404 })
    );
  }
} satisfies ExportedHandler<Env>;
```

#### 6. `wrangler.jsonc`
Configuration for Cloudflare Workers with Assets and Durable Objects:
```jsonc
{
  "name": "repro-issue-<issueNumber>",
  "main": "src/server.ts",
  "compatibility_date": "2026-06-11",
  "compatibility_flags": ["nodejs_compat"],
  "assets": {
    "not_found_handling": "single-page-application",
    "run_worker_first": ["/agents/*"]
  },
  "durable_objects": {
    "bindings": [{ "name": "ReproAgent", "class_name": "ReproAgent" }]
  },
  "migrations": [
    { "tag": "v1", "new_sqlite_classes": ["ReproAgent"] }
  ]
}
```

#### 7. `tsconfig.json`
```json
{
  "extends": "agents/tsconfig"
}
```

### Critical Rules
- **Asset Directory**: Never set `assets.directory`. The Vite plugin manages client output.
- **Build Sequence**: Always run `vite build` prior to `wrangler deploy`.
- **SPA Fallbacks**: `run_worker_first` must explicitly list `/agents/*` so agent routes are not intercepted by the client index fallback.
- **SQLite Migrations**: Use `new_sqlite_classes` since Agents require SQLite-backed Durable Objects.

---

## 5. Phase 4: Deploying to a Temporary Cloudflare Account

Because no static Cloudflare credentials exist in the environment, use wrangler's temporary preview account deployment:

```bash
mkdir -p /temp
npm install > /temp/install.log 2>&1 || (tail -30 /temp/install.log; false)

# Deploy to temporary preview account
npm run deploy # executes: vite build && wrangler deploy --temporary
```

Capture the resulting `https://...workers.dev` URL as `liveUrl`.

---

## 6. Phase 5: Verifying the Reproduction

Test both the UI and the backend endpoint:

```bash
# Verify UI is responding (HTTP 200)
curl -sS -i "<liveUrl>/" | head -5

# Trigger the bug endpoint
curl -sS -i "<liveUrl>/agents/repro-agent/demo<triggerPath>"
```

- Set `reproduced: true` only if the observed symptom matches the reported bug.
- If behavior is normal, set `reproduced: false` and note that the issue may already be resolved or requires additional parameters.

---

## 7. Phase 6: Publishing the Orphan Branch

Publish the reproduction project as an isolated orphan branch so maintainers and fix agents can clone it directly without repository history bloat:

```bash
PUBLISH_DIR="/workspace/repro-publish-<issueNumber>"
mkdir -p "$PUBLISH_DIR" && cd "$PUBLISH_DIR"

# Initialize clean orphan branch
git init -q -b repro/issue-<issueNumber>

# Copy files excluding build artifacts and secrets
tar -C "$REPRO_DIR" \
  --exclude node_modules \
  --exclude dist \
  --exclude .wrangler \
  --exclude .env -cf - . | tar -xf -

git add -A
git commit -q -m "repro for #<issueNumber>: <one-line issue title>"
git push -f https://github.com/<repo>.git HEAD:repro/issue-<issueNumber>

cd /workspace && rm -rf "$PUBLISH_DIR"
```

Capture `https://github.com/<repo>/tree/repro/issue-<issueNumber>` as `reproBranchUrl`.

---

## 8. Phase 7: Issue Reporting & Result Schema

### Issue Comment Template
Post a detailed comment using `gh issue comment`:
```bash
gh issue comment <issueNumber> --repo <repo> --body-file comment.md
```

**Comment Content**:
1. `Requested by @<requestedBy>` mention.
2. **Verdict**: (Reproduced / Could not reproduce / Skipped) with concise justification.
3. **Live URL**:
   > Repro URL (expires after 60 mins): `<liveUrl>`
   > *Instructions on how to test using the UI.*
4. **Repro Branch**: Link to `reproBranchUrl` for easy local checkout.
5. **Minimal Repro Code**: Key snippets of `server.ts` and `wrangler.jsonc`.
6. **Observed vs. Expected**: Error output, status codes, or logs.
7. **Root-Cause Hypothesis**: Suspected file and line number in `packages/`.
8. **Footer**: `🤖 generated by the repro-agent`.

### Structured Return Schema
```typescript
type ReproduceResult = {
  reproduced: boolean;
  skipped: boolean;
  summary: string;
  liveUrl?: string;
  reproBranchUrl?: string;
  rootCauseHypothesis?: string;
  commentUrl?: string;
};
```
