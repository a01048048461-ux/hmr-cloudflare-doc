# Commands, Toolchain & Build Pipeline

## 1. Toolchain Overview (Vite+)

Kumo uses **Vite+** (`vite-plus` / `vp` CLI) as a unified toolchain for bundling, testing, linting, and formatting:

| Capability | Engine | Configuration |
| :--- | :--- | :--- |
| **Linting** | Oxlint (`vp lint`) | Custom rules in `lint/` + `vite.config.ts` |
| **Formatting** | Oxfmt (`vp fmt`) | Replaces Prettier; configured in `vite.config.ts` |
| **Testing** | Vitest (`vp test`) | Happy-dom environment, v8 coverage |
| **Packaging** | Vite 8 + tsdown (`vp pack`) | ESM library mode (kumo), Astro docs |

---

## 2. Essential Commands

### Repo-Wide Quality & Dev
```bash
# Start Astro documentation dev server (localhost:4321)
pnpm dev

# Run oxlint across all packages (includes custom rules)
pnpm lint

# TypeScript verification across all packages
pnpm typecheck

# Full check (formatting + linting)
pnpm vp check
```

### Target Package Operations
```bash
# Build the @cloudflare/kumo library
pnpm --filter @cloudflare/kumo build

# Run Vitest test suite for @cloudflare/kumo
pnpm --filter @cloudflare/kumo test

# Regenerate component registry
pnpm --filter @cloudflare/kumo codegen:registry

# Build the Figma plugin
pnpm --filter @cloudflare/kumo-figma build
```

---

## 3. Cross-Package Build & Codegen Pipeline

There is a sequential dependency between documentation demos, the AI registry, and Figma assets:

```text
kumo-docs-astro demos
       ↓ (extracts demo code)
dist/demo-metadata.json
       ↓
kumo codegen:registry
       ↓ (generates schemas & registry)
ai/component-registry.{json,md} + ai/schemas.ts
       ↓
kumo-figma build:data
       ↓
generated/*.json → vp pack (tsdown) → code.js (IIFE, ES2017)
```

> [!IMPORTANT]
> Because registry codegen consumes metadata from Astro documentation demos, run `codegen:demos` in `packages/kumo-docs-astro` before running `codegen:registry` in `packages/kumo`.
