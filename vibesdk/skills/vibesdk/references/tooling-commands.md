# Tooling, Verification & Change Paths Reference

## Bun Toolchain

Always execute commands using **Bun** from the workspace root:

```bash
bun run setup             # Interactive bootstrap of Cloudflare resources
bun run dev               # Starts React frontend + Worker together (localhost:5173)
bun run dev:browser       # Optional Chromium sidecar for think agent
bun run typecheck         # Full TypeScript check
bun run lint              # ESLint (checks src/** and worker/**)
bun run test              # Vitest suite (using Workers pool)
bun run build             # Builds space and Vite/Worker bundle
```

---

## Targeted Subpackage Workflows

* **Space Package**: `bun run --cwd space typecheck` / `bun run --cwd space build`
* **SDK Package**: `bun run --cwd sdk test` / `bun run --cwd sdk package`
* **Database Migrations**:
  ```bash
  bun run db:generate     # Generate migrations from worker/database/schema.ts
  bun run db:migrate:local # Apply migrations locally
  ```
* **Binding Types**: `bun run cf-typegen` generates `worker-configuration.d.ts`.

---

## Change Checklist

1. **API Endpoints**: `src/api-types.ts` -> `src/lib/api-client.ts` -> `worker/database/services/` -> `worker/api/controllers/` -> `worker/api/routes/`.
2. **WebSocket Messages**: `worker/api/websocketTypes.ts` -> `worker/agents/core/websocket.ts` -> `src/routes/chat/utils/`.
3. **Agent Tools**: Under `worker/agents/tools/toolkit/` and registered in `customTools.ts`.
