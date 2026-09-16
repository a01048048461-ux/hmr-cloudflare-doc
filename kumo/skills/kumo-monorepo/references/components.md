# Kumo Component Architecture & Registry

## 1. Scaffolding New Components

Never manually create component directories or files from scratch. Kumo maintains code generators and plop injection markers (`PLOP_INJECT_EXPORT`, `PLOP_INJECT_COMPONENT_ENTRY`):

```bash
pnpm --filter @cloudflare/kumo new:component
```

The scaffolding wizard will:
- Generate component boilerplate with proper TypeScript types
- Set up test files
- Register exports in package entrypoints
- Establish correct forwardRef and displayName patterns

---

## 2. Component API & Registry (Single Source of Truth)

Before modifying or implementing a component, always inspect the component registry:
* File: `packages/kumo/ai/component-registry.json` (and `component-registry.md`)
* This registry is automatically generated at build time and documents all component props, variants, and slots.

To regenerate after component changes:
```bash
pnpm --filter @cloudflare/kumo codegen:registry
```

---

## 3. Primitives vs. Blocks vs. Components

Understanding package boundaries in Kumo:

* **Core Components (`packages/kumo/src/components/{name}/`)**:
  - The published UI components (`@cloudflare/kumo`).
  - Built on Base UI headless primitives and styled with Kumo tokens.
* **Primitives (`packages/kumo/src/primitives/`)**:
  - 40+ auto-generated re-exports from Base UI.
* **Blocks (`packages/kumo/src/blocks/`)**:
  - Pre-assembled layouts and complex UI patterns.
  - **NOT exported from the npm library index.**
  - Installed directly into consuming applications via the Kumo CLI (`kumo add <block>`).
* **Catalog (`packages/kumo/src/catalog/`)**:
  - Runtime JSON-UI rendering engine (separate concern from standard components).

---

## 4. Component Implementation Invariants

* **`displayName`**: Always set `.displayName` on `forwardRef` components (required for React DevTools and automated testing).
* **Never edit auto-generated files directly**:
  - `theme-kumo.css` → edit `scripts/theme-generator/config.ts`
  - `ai/schemas.ts` and `ai/component-registry.*` → run registry codegen
