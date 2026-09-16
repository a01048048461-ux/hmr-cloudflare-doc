---
name: kumo-monorepo
description: >-
  Official development, styling, and architectural playbook for the Cloudflare Kumo component library monorepo (@cloudflare/kumo).
  Use when creating or modifying UI components, styling with semantic tokens (bg-kumo-base, text-kumo-default),
  running Vite+ (vp) toolchain commands, managing the component registry, or handling changesets and PR descriptions.
---

# Kumo Component Library Monorepo Skill

This skill provides the authoritative engineering playbook for developing, styling, and maintaining Cloudflare's **Kumo** React component library (`@cloudflare/kumo`).

---

## Progressive Disclosure References

Detailed specifications and runbooks are modularized in `references/`:

| Topic | Reference Document | Focus Area |
| :--- | :--- | :--- |
| **Styling & Tokens** | [references/styling.md](./references/styling.md) | Semantic tokens, `light-dark()`, no `dark:` prefix, surface depth |
| **Components** | [references/components.md](./references/components.md) | Scaffolding (`new:component`), Base UI primitives, component registry |
| **Commands & Pipeline** | [references/commands-pipeline.md](./references/commands-pipeline.md) | Vite+ (`vp lint/fmt/test`), cross-package build pipeline |
| **Contributing & PRs** | [references/contributing.md](./references/contributing.md) | Changeset rules, `.vite-hooks`, CI-enforced PR description checklist |

---

## Core Engineering Invariants

### 1. Styling Rule: Semantic Tokens Only
* **ALWAYS use semantic tokens**: `bg-kumo-base`, `bg-kumo-elevated`, `text-kumo-default`, `border-kumo-line`.
* **NEVER use raw Tailwind colors**: `bg-blue-500` or `text-gray-900` violate design system constraints and fail Oxlint.
* **NEVER use the `dark:` variant prefix**: Dark mode is automatic via native `light-dark()` CSS variables.
* **Exceptions**: `bg-white`, `bg-black`, `text-white`, `text-black`, `transparent`.
* **Class composition**: Always merge classes via `cn("base", condition && "extra", className)`.

### 2. Component Scaffolding
* **Scaffold with CLI**:
  ```bash
  pnpm --filter @cloudflare/kumo new:component
  ```
  Never create component directories manually. The scaffolding tool maintains essential plop markers and entrypoint registrations.
* **Check Registry First**: Inspect `packages/kumo/ai/component-registry.json` before modifying component APIs.

### 3. Toolchain & Quality Checks
* **Run Linter**: `pnpm lint` (Oxlint with custom Kumo AST rules).
* **Run Typecheck**: `pnpm typecheck` (TypeScript 5.9).
* **Format**: `pnpm vp fmt` (Oxfmt).
* **Run Tests**: `pnpm --filter @cloudflare/kumo test` (Vitest with happy-dom).

---

## Rapid Workflow Checklist

1. **Before pushing changes**:
   * If `packages/kumo/` was modified: run `pnpm changeset` (enforced by pre-push hook).
   * Verify linting and formatting: `pnpm vp check`.
   * Verify types: `pnpm typecheck`.
2. **Creating PRs**:
   * Include the mandatory review & testing checklist in the PR body (see [contributing.md](./references/contributing.md)).

---

## Boundaries

### Always
* Use semantic tokens (`bg-kumo-*`, `text-kumo-*`) for all styling.
* Set `.displayName` on all `forwardRef` components.
* Enforce ESM-only syntax (`"type": "module"`).
* Scaffold new components using `pnpm --filter @cloudflare/kumo new:component`.

### Ask First
* Adding any external npm dependency to `packages/kumo`.
* Altering the semantic color token definitions in `scripts/theme-generator/config.ts`.
* Updating root Vite+ or Astro configurations.

### Never
* **Never** commit secrets, Figma access tokens, or npm credentials.
* **Never** use raw Tailwind colors (`bg-blue-500`) or `dark:` prefixes.
* **Never** use relative cross-package imports (use `@cloudflare/kumo`, not `../../kumo/src/...`).
* **Never** edit auto-generated files directly (`theme-kumo.css`, `ai/schemas.ts`, `ai/component-registry.*`).
* **Never** run publishing/release commands (`pnpm release`, `pnpm publish:beta`).
