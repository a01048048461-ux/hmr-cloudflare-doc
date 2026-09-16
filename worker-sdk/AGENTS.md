# Cloudflare Workers SDK — Project Rules

This monorepo contains Cloudflare's core developer tools: Wrangler CLI, Miniflare simulator, Create-Cloudflare (C3), and Vite/Vitest plugins. Complete engineering guides, package topologies, and Turborepo workflows are in the **`workers-sdk` skill** at [`.agents/skills/workers-sdk/SKILL.md`](SKILL.md).

---

## High-Frequency Commands

* **Build**: `pnpm build` (Turbo) or `pnpm run build --filter <package>`
* **Validation**: `pnpm check` (sherif, oxlint, typecheck, format)
* **Testing**: `pnpm test:ci` or `pnpm -w test:ci -F <package> -- <test-file>`
* **Format**: `pnpm prettify` (oxfmt)
* **Changesets**: `pnpm changeset`

---

## Repository Map Summary

* `packages/wrangler/`: Wrangler CLI implementation
* `packages/miniflare/`: Local Workers simulator & `workerd` runtime binding
* `packages/create-cloudflare/`: C3 project initialization wizard
* `packages/vite-plugin-cloudflare/`: `@cloudflare/vite-plugin`
* `packages/vitest-plugin/`: `@cloudflare/vitest-pool-workers`

---

## Boundaries

* **Always**: Use `pnpm` and run commands from the workspace root.
* **Never**: Edit generated files directly.
* **Never**: Commit secrets or credentials.

> See full details in [`.agents/skills/workers-sdk/SKILL.md`](SKILL.md).
