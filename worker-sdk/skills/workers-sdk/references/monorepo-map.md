# Workers SDK Monorepo Map

## Package Breakdown

| Directory | Package / Component | Purpose |
| :--- | :--- | :--- |
| `packages/wrangler/` | `wrangler` | The official Cloudflare developer CLI (`src/index.ts`) |
| `packages/miniflare/` | `miniflare` | Local Workers simulator (`workerd` integration) |
| `packages/create-cloudflare/` | `create-cloudflare` (C3) | Project initialization and framework templates |
| `packages/vite-plugin-cloudflare/` | `@cloudflare/vite-plugin` | Vite plugin integrating Workers runtime into Vite |
| `packages/vitest-plugin/` | `@cloudflare/vitest-pool-workers` | Vitest testing environment running inside `workerd` |
| `packages/workers-utils/` | Shared utilities | Configuration normalization, shared test helpers |
| `packages/deploy-helpers/` | Deploy utilities | Validation of worker deploy properties |
| `fixtures/` | Test fixtures | Workspace fixture packages for integration testing |

---

## Modifying Wrangler Commands

Wrangler commands are registered in `packages/wrangler/src/index.ts`. When creating or editing commands:
* Command handlers reside under `packages/wrangler/src/`.
* Argument parsing uses `yargs`.
* Always add corresponding unit/integration tests in `packages/wrangler/src/__tests__/`.
