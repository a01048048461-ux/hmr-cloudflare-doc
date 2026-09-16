# Architecture, Boundaries & Data Flow Reference

## Monorepo Boundaries

* **`src/`**: React client application (`src/main.tsx`, routes in `src/routes.tsx`).
  - API contracts in `src/api-types.ts`
  - Frontend HTTP client in `src/lib/api-client.ts`
* **`worker/`**: Cloudflare Worker runtime and Durable Object exports (`worker/index.ts`).
  - Hono routes in `worker/app.ts` and `worker/api/routes/`
  - Agent tools in `worker/agents/tools/`
  - D1 database schema in `worker/database/schema.ts`
* **`space/`**: Dedicated workspace package providing `SpaceDO` (git history over Cloudflare Artifacts).
  - Edit `space/src/`, never generated `space/dist/`.
* **`sdk/`**: Independent Bun package communicating over platform WebSockets (`worker/api/websocketTypes.ts`).

---

## Data Fetching & State Invariants

* **TanStack Query**: Primary server state manager. Centralize query keys in `src/lib/query-keys.ts`.
* **Centralized API Client**: Query functions must wrap `apiClient` methods; do not call `fetch` directly from components.
* **Cache Invalidation**: Mutations must update query cache via `queryClient.setQueryData` or invalidate hierarchical keys.
* **UI Component Preference**: Prefer `@cloudflare/kumo` primitives over legacy `src/components/ui/` components.
