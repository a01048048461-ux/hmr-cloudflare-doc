---
name: workers-sdk
description: >-
  Official development, testing, and operational skill for Cloudflare's core Workers SDK monorepo (Wrangler, Miniflare, C3, Vite/Vitest plugins).
  Use when developing CLI commands, changing local development/workerd behavior, updating templates, or running Turbo tasks.
---

# Cloudflare Workers SDK Monorepo Skill

Engineering manual for developing within the official `workers-sdk` monorepo.

---

## Progressive Disclosure References

| Topic | Reference | Focus Area |
| :--- | :--- | :--- |
| **Monorepo Map** | [references/monorepo-map.md](./references/monorepo-map.md) | Package topology (`wrangler`, `miniflare`, `create-cloudflare`, plugins) |
| **Toolchain & Turbo** | [references/toolchain-turborepo.md](./references/toolchain-turborepo.md) | Turborepo commands, filtered runs, Oxlint, Changesets |

---

## Daily Workflow Checklist

1. **Developing Features**:
   * Run targeted builds: `pnpm run build --filter <package>`
   * Run targeted tests: `pnpm -w test:ci -F <package> -- <test-file>`
2. **Quality Verification**:
   * Run `pnpm check` and `pnpm prettify`.
3. **Contributing**:
   * Generate changesets for published package modifications via `pnpm changeset`.

---

## Boundaries

### Always
* Use `pnpm` exclusively (never npm or yarn).
* Run commands from the workspace root unless package docs specify otherwise.
* Read package-level `AGENTS.md` before changing package internals.

### Never
* Never edit auto-generated files directly.
* Never commit secrets, credentials, or production tokens.
* Never run credentialed E2E tests (`pnpm test:e2e`) in unauthenticated environments.
