# Toolchain, Turborepo & Quality Commands

## Monorepo Toolchain

* **Package Manager**: `pnpm` (use exact version in `package.json`)
* **Orchestration**: Turborepo (`turbo.json`)
* **Linters/Formatters**: Oxlint (`.oxlintrc.jsonc`) & Oxfmt (`.oxfmtrc.jsonc`)

---

## Workspace Commands

```bash
# Build entire workspace with Turbo
pnpm build

# Run CI validation suite (checks, lints, types, format)
pnpm check

# Run tests in CI mode
pnpm test:ci

# Format repository files
pnpm prettify

# Run supported automated fixes
pnpm fix
```

---

## Targeted Package Operations

Target single packages using Turbo filters:

```bash
# Run build for a single package (e.g. wrangler)
pnpm run build --filter wrangler

# Run specific test file inside a package
pnpm -w test:ci -F wrangler -- src/__tests__/index.test.ts
```

---

## Changesets

Any modifications to published packages (`wrangler`, `miniflare`, etc.) require a changeset:
* Consult `.changeset/README.md`
* Run `pnpm changeset` from the workspace root
