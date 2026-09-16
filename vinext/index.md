# vinext Documentation Index

Index of all architecture documentation, migration guides, compatibility matrices, and agent skills for **vinext** — running Next.js applications on Vite with Cloudflare Workers as the primary deployment target.

## Core Documents

| Document | Type | Description |
| --- | --- | --- |
| [AGENTS.md](./AGENTS.md) | Agent Guide | Complete development principles, architecture, RSC/Server Action pipelines, and test suites |
| [README.md](./README.md) | Overview | Feature status, App/Pages router support, quickstart, C3 integration, and known gaps |

---

## Migration Skills & References (`skills/`)

### Migration Skill
| Guide | Type | Description |
| --- | --- | --- |
| [migrate-to-vinext](./skills/migrate-to-vinext/SKILL.md) | Agent Skill | Step-by-step automated workflow for migrating existing Next.js projects to vinext |

### Deep-Dive References (`skills/migrate-to-vinext/references/`)
| Reference | Topic | Description |
| --- | --- | --- |
| [Compatibility Matrix](./skills/migrate-to-vinext/references/compatibility.md) | Compatibility | Comprehensive breakdown of Next.js features, supported APIs, and current limitations |
| [Configuration Examples](./skills/migrate-to-vinext/references/config-examples.md) | Configuration | Production configurations for `vite.config.ts`, `wrangler.jsonc`, Cloudflare bindings, and caching |
| [Troubleshooting Guide](./skills/migrate-to-vinext/references/troubleshooting.md) | Debugging | Solutions for common migration issues: RSC errors, native module mismatches, and route handler quirks |
