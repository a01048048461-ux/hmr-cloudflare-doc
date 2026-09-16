# AGENTS.md — Cloudflare Agentic AI Workspace

Operating guidelines and repository conventions for AI coding assistants working in `hmr-cloudflare-agent`.

---

## 1. Ecosystem Architecture & Subsystems

This workspace consolidates Cloudflare''s complete modern developer toolchain, agentic frameworks, UI components, and container runtime platforms:

```
┌────────────────────────────────────────────────────────────────────────┐
│                        hmr-cloudflare-agent                            │
├────────────────────────────────┬───────────────────────────────────────┤
│ Core Agent Frameworks          │ Developer Infrastructure & Tooling    │
│  • agents-sdk                  │  • worker-sdk (Wrangler, Miniflare)   │
│  • cloudflare-os (Gatekeepers) │  • sandbox-sdk (Containers)           │
│  • vibesdk (Full-Stack Maker)  │  • vinext (Next.js on Vite)           │
│                                │  • kumo (Base UI Design System)       │
│                                │  • templates (38 Production Starters) │
│                                │  • mcp-server.md (Cloudflare MCP)     │
└────────────────────────────────┴───────────────────────────────────────┘
```

### Subsystem Directory Map

| Directory | Scope & Purpose | Primary Technology |
| --- | --- | --- |
| **`agents-sdk/`** | Core Cloudflare Agents framework, turn execution, state, and skills | Durable Objects, SQLite, `@cloudflare/think` |
| **`cloudflare-os/`** | Enterprise AI productivity OS, Gatekeeper security guardrails, gadgets | Cloudflare Workers, Durable Objects, Access |
| **`kumo/`** | Cloudflare''s official UI component library built on Base UI | React 19, Base UI, CSS Modules |
| **`sandbox-sdk/`** | Isolated Linux container execution inside Cloudflare Workers | Docker, MicroVMs, WebSocket Bridge |
| **`templates/`** | 38 production starter templates for full-stack, AI, and backend apps | Cloudflare Workers, D1, Hyperdrive, KV, R2 |
| **`vibesdk/`** | Autonomous platform for building and deploying full-stack apps via AI | ThinkAgent, SpaceDO, Dynamic Workers, Facets |
| **`vinext/`** | Reimplementation of Next.js App and Pages router on Vite for Workers | Vite, React Server Components (RSC) |
| **`worker-sdk/`** | Official developer toolchain: Wrangler CLI, Miniflare, and C3 | Node.js, TypeScript, workerd C++ binding |

---

## 2. Engineering Guidelines for AI Agents

### 1. The Three-File Standard
Every primary directory and submodule within this repository must maintain the following three root documentation files:
1. `AGENTS.md`: Technical context, boundaries, architecture instructions, and AI rules.
2. `README.md`: Human-facing overview, quickstart, and conceptual explanation.
3. `index.md`: Comprehensive table of contents and link directory for all files and submodules.

### 2. Monorepo Command Conventions
- **Package Manager**: Use `pnpm` exclusively across all packages (do not use npm or yarn unless testing template scaffolding).
- **Session Protection**: Long-running or verbose commands (`pnpm install`, `pnpm build`, full test suites) must redirect output to `/temp` or container logs (e.g. `> /temp/build.log 2>&1; tail -30 /temp/build.log`) to avoid terminal buffer overflow.
- **Targeted Execution**: Prefer scoped commands (e.g. `pnpm --filter <package> test` or Turbo filter syntax) over full repository passes.

### 3. Component Boundaries & Isolation
- Keep package dependencies clean. Do not introduce circular dependencies between standalone modules (e.g. `kumo` should remain UI-focused and agnostic of specific agent backends).
- In `sandbox-sdk`, adhere to the three-layer boundary: Worker client, RPC bridge, and container-internal daemon.
- In `templates`, maintain single-file or self-contained structures to ensure templates remain zero-overhead starter points.

### 4. Security & Safety
- **Never** commit secrets, API keys, or production tokens to git.
- Adhere to the Gatekeeper security model when generating code for `cloudflare-os`: all sensitive tools must be guarded by policy checks and human-in-the-loop approvals.
