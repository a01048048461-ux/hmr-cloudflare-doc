# Cloudflare Workers SDK Documentation Index

Index of all architecture documentation, developer guidelines, package maps, and monorepo engineering skills for the **Cloudflare Workers SDK** (`workers-sdk`).

## Core Documents

| Document | Type | Description |
| --- | --- | --- |
| [AGENTS.md](./AGENTS.md) | Agent Guide | High-frequency commands, repository boundaries, Turborepo rules, and AI assistant guidelines |
| [README.md](./README.md) | Overview | Quickstart with C3 (`create-cloudflare`), official documentation links, and community resources |

---

## Skills & Engineering References (`skills/`)

### Workers SDK Skill
| Guide | Type | Description |
| --- | --- | --- |
| [workers-sdk Skill](./skills/workers-sdk/SKILL.md) | Operational Skill | Engineering manual for developing within the official `workers-sdk` monorepo |

### Progressive Disclosure References (`skills/workers-sdk/references/`)
| Reference | Topic | Description |
| --- | --- | --- |
| [Monorepo Map](./skills/workers-sdk/references/monorepo-map.md) | Package Topology | Deep-dive guide to packages: `wrangler`, `miniflare`, `create-cloudflare`, Vite/Vitest plugins |
| [Toolchain & Turborepo](./skills/workers-sdk/references/toolchain-turborepo.md) | Build System | Turborepo pipeline, filtered execution, caching, Oxlint, Prettier, and Changeset workflows |

---

## Core Monorepo Packages

The `workers-sdk` monorepo houses Cloudflare's official developer toolchain:

| Package | Role | Key Capabilities |
| --- | --- | --- |
| `packages/wrangler` | CLI Tool | Development, bundling, deployment, logs, KV/D1/R2 management, and temporary preview accounts |
| `packages/miniflare` | Local Simulator | Local execution engine powered by the `workerd` C++ runtime binding |
| `packages/create-cloudflare` | Project Wizard | `c3` CLI for scaffolding modern full-stack web applications and Workers |
| `packages/vite-plugin-cloudflare` | Vite Plugin | Running server-side Worker code inside Vite development servers and bundling builds |
| `packages/vitest-plugin` | Vitest Pool | `@cloudflare/vitest-pool-workers` for isolated unit and integration testing in workerd |
