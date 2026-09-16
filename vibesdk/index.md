# Cloudflare VibeSDK Documentation Index

Index of all architecture guides, setup instructions, skills, and API documentation for **VibeSDK** — the autonomous full-stack app-building platform powered by Cloudflare Think, Durable Objects, Dynamic Workers, and Facets.

## Core Documents

| Document | Type | Description |
| --- | --- | --- |
| [AGENTS.md](./AGENTS.md) | Agent Guide | Operational boundaries, tool access rules, and coding assistant instructions |
| [README.md](./README.md) | Overview | System capabilities, component topology, ThinkAgent loop, and Dynamic Worker previews |


---

## Technical Documentation (`docs/`)

| Document | Category | Description |
| --- | --- | --- |
| [Setup & Deployment](./docs/setup.md) | Guide | Local development setup, Cloudflare bindings, and deployment to production |
| [Architecture Diagrams](./docs/architecture-diagrams.md) | Architecture | Detailed Mermaid component diagrams, data flows, and state synchronization |
| [LLM & Prompt Architecture](./docs/llm.md) | AI Core | System prompts, model coordination, tool definitions, and token optimization |
| [Usage Limits UI](./docs/usage-limits-ui.md) | Product / Billing | Managing user quotas, billing tiers, and usage restriction interfaces |
| [Postman API Collection](./docs/POSTMAN_COLLECTION_README.md) | API Testing | Guide to using the Postman collections and testing backend endpoints |

---

## Skills & Reference Architecture (`skills/`)

| Guide | Description |
| --- | --- |
| [vibesdk Skill](./skills/vibesdk/SKILL.md) | End-to-end guidance for agents developing inside the VibeSDK codebase |
| [Architecture Data](./skills/vibesdk/references/architecture-data.md) | Data schemas, SQLite storage layout, and SpaceDO state management |
| [Tooling Commands](./skills/vibesdk/references/tooling-commands.md) | CLI commands, build scripts, bundler flags, and Vitest test suites |
