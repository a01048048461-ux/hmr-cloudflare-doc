# AGENTS.md — packages/

Guidelines and monorepo standards for AI agents working across the core packages of the Cloudflare Agents SDK.

## Monorepo Architecture

The repository is organized as a pnpm monorepo managed with Nx. Each directory in `packages/` publishes an independent, scoped npm package under the `@cloudflare` organization.

### Dependency Graph

```
┌────────────────────────────────────────────────────────┐
│                      @cloudflare/think                 │
│         (Autonomous turns, lifecycle, messengers)       │
└────────────────┬──────────────────────┬────────────────┘
                 │                      │
                 ▼                      ▼
┌─────────────────────────┐   ┌──────────────────────────┐
│  @cloudflare/codemode   │   │    @cloudflare/voice     │
│   (Isolated execution)  │   │  (Realtime audio streams)│
└────────────────┬────────┘   └─────────┬────────────────┘
                 │                      │
                 ▼                      ▼
┌────────────────────────────────────────────────────────┐
│                 @cloudflare/agents                     │
│    (Core Agent, Durable Objects, State, Routing, RPC)  │
└────────────────┬──────────────────────┬────────────────┘
                 │                      │
                 ▼                      ▼
┌─────────────────────────┐   ┌──────────────────────────┐
│   @cloudflare/shell     │   │ @cloudflare/hono-agents  │
│(SQLite+R2 Workspace VFS)│   │ (Hono middleware/routes) │
└─────────────────────────┘   └──────────────────────────┘
```

## Package Rules for Agents

1. **Scoped Isolation**: Keep packages decoupled. Shared utilities should live in `@cloudflare/agents` or a dedicated shared internal module.
2. **TypeScript & Bundling**: All packages extend the root `tsconfig.base.json`. Bundling is handled via `tsup` or custom build scripts producing ESM output.
3. **Changesets**: When modifying package source code in a user-facing way, create a changeset using `pnpm changeset`.
4. **Noisy Command Discipline**: When running monorepo commands (`pnpm install`, `pnpm --filter <pkg> test`), redirect output to `/temp` to prevent session buffer overflow.
