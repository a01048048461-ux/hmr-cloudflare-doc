---
name: vibesdk
description: >-
  Development manual and operational skill for VibeSDK (Cloudflare Vibe Coding platform, ThinkAgent, SpaceDO).
  Use when developing React frontends (Kumo + Tailwind v4), Worker Durable Objects, SpaceDO workspaces, TanStack Query hooks, or Bun scripts.
---

# VibeSDK Monorepo Skill

Engineering manual for developing and contributing to VibeSDK.

---

## Progressive Disclosure References

| Topic | Reference | Focus Area |
| :--- | :--- | :--- |
| **Architecture & Data** | [references/architecture-data.md](./references/architecture-data.md) | Package boundaries (`src`, `worker`, `space`, `sdk`), TanStack Query, Kumo UI |
| **Tooling & Commands** | [references/tooling-commands.md](./references/tooling-commands.md) | Bun commands, database migrations, change paths, D1 schema |

---

## Core Invariants

1. **Bun Everywhere**: Always use Bun from the repo root (`bun run dev`, `bun run build`).
2. **Kumo First**: Prefer `@cloudflare/kumo` primitives over legacy UI components.
3. **No Any**: Avoid introducing new `any` types; import or declare strict types in `src/api-types.ts`.
4. **Owner-Only API**: All `/api/*` routes are authenticated and owner-only by default.
5. **Never Commit Secrets**: Never commit `.dev.vars*` or `.prod.vars`.

---

## Boundaries

### Always
* Run `bun run typecheck` and `bun run lint` when concluding tasks.
* Use `apiClient` methods for frontend network requests.
* Run `bun run cf-typegen` after updating Wrangler bindings.

### Never
* Never commit environment secret files.
* Never edit generated files in `space/dist/`.
