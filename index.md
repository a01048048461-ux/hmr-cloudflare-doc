# Cloudflare Agentic AI Workspace — Master Index

Comprehensive directory index, architecture catalog, and documentation map for the entire `hmr-cloudflare-agent` repository.

---

## Workspace Root Documents

| Document | Type | Scope |
| :--- | :--- | :--- |
| **[AGENTS.md](./AGENTS.md)** | Master AI Guide | System topology, boundaries, command conventions, and rules for AI coding assistants |
| **[README.md](./README.md)** | Workspace Overview | High-level summary of the 8 subsystems, architectural diagram, and developer quickstart |
| **[mcp-server.md](./mcp-server.md)** | Reference | Specifications and connection URLs for Cloudflare''s Model Context Protocol (MCP) servers |

---

## 1. Core Agent Framework (`agents-sdk/`)

The foundational framework for building stateful, durable, and autonomous AI agents on Cloudflare Workers.

| Subsystem / Area | Documentation | Scope & Key Capabilities |
| :--- | :--- | :--- |
| **[agent-think](./agents-sdk/skill/agent-think/)** | [Index](./agents-sdk/skill/agent-think/index.md) | Autonomous issue triage, repro scaffolding, and PR creation agent |
| **[design](./agents-sdk/skill/design/)** | [Index](./agents-sdk/skill/design/index.md) | 36 architectural records, RFCs, and tradeoffs across the Agents SDK |
| **[docs](./agents-sdk/skill/docs/)** | [Index](./agents-sdk/skill/docs/index.md) | Official developer guides, Diátaxis tutorials, and API references |
| **[examples](./agents-sdk/skill/examples/)** | [Index](./agents-sdk/skill/examples/index.md) | 55 runnable reference applications demonstrating SDK features |
| **[experimental](./agents-sdk/skill/experimental/)** | [Index](./agents-sdk/skill/experimental/index.md) | Future-facing prototypes: gadgets, fibers, chat recovery, and gateway resumption |
| **[openai-sdk](./agents-sdk/skill/openai-sdk/)** | [Index](./agents-sdk/skill/openai-sdk/index.md) | Running `@openai/agents` inside Cloudflare Durable Objects |
| **[packages](./agents-sdk/skill/packages/)** | [Index](./agents-sdk/skill/packages/index.md) | Monorepo package specifications (`@cloudflare/agents`, `think`, `codemode`, etc.) |
| **[pattern-oriented](./agents-sdk/skill/pattern-oriented/)** | [Index](./agents-sdk/skill/pattern-oriented/index.md) | In-depth architectural tutorials (Anthropic patterns, Human-in-the-Loop) |
| **[voice-providers](./agents-sdk/skill/voice-providers/)** | [Index](./agents-sdk/skill/voice-providers/index.md) | Realtime speech and telephony integrations (Deepgram, ElevenLabs, Twilio) |

---

## 2. Enterprise AI Operating System (`cloudflare-os/`)

An AI productivity environment featuring Gatekeeper security guardrails, sandboxed gadgets, and blueprints.

| Resource | Path | Description |
| :--- | :--- | :--- |
| **Overview & Setup** | [README.md](./cloudflare-os/README.md) | Quickstart (`pnpm run-local`), gadgets, blueprints, and local workerd runtime |
| **Agent Guidelines** | [AGENTS.md](./cloudflare-os/AGENTS.md) | System architecture, Durable Object topology, security guardrails, and boundaries |
| **Documentation Index** | [index.md](./cloudflare-os/index.md) | Catalog of architectural specifications and Gatekeeper skills |
| **Technical Specs** | `docs/` | Observers, sharing permissions, AI gateway billing, OAuth, and integration testing |
| **Skills** | `skills/` | [write-gatekeeper](./cloudflare-os/skills/write-gatekeeper/SKILL.md) for authoring security guardrails |

---

## 3. Design System & Component Library (`kumo/`)

Cloudflare''s accessible UI component library built on Base UI with semantic tokens and CSS Modules.

| Resource | Path | Description |
| :--- | :--- | :--- |
| **Overview & Installation** | [README.md](./kumo/README.md) | Package installation, tree-shaking, Base UI primitives, and CLI tool |
| **Agent Guidelines** | [AGENTS.md](./kumo/AGENTS.md) | Component patterns, CSS Modules, semantic color tokens, and Figma synchronization |
| **Component Index** | [index.md](./kumo/index.md) | Complete directory of styling guides, skills, and monorepo references |
| **Engineering Skills** | `skills/` | `kumo-design`, `kumo-monorepo`, and component documentation references |

---

## 4. Container Sandboxing Platform (`sandbox-sdk/`)

Isolated Linux container execution inside Cloudflare Workers (`@cloudflare/sandbox`).

| Resource | Path | Description |
| :--- | :--- | :--- |
| **Overview & Quickstart** | [README.md](./sandbox-sdk/README.md) | Installation, Dockerfile configuration, and basic Worker usage |

| **Agent Guidelines** | [AGENTS.md](./sandbox-sdk/AGENTS.md) | Three-layer model, monorepo commands, testing guidelines, and boundaries |
| **Documentation Index** | [index.md](./sandbox-sdk/index.md) | Catalog of technical docs (Session Execution, Concurrency, Jupyter, OpenAI) and skills |

---

## 5. Production Starter Templates (`templates/`)

A curated collection of 38 production-ready starter templates for Cloudflare Workers.

| Resource | Path | Description |
| :--- | :--- | :--- |
| **Overview & Testing** | [README.md](./templates/README.md) | Getting started with C3 (`create-cloudflare`), dashboard deployment, and Playwright tests |
| **Agent Guidelines** | [AGENTS.md](./templates/AGENTS.md) | Template contribution standards, testing requirements, and directory rules |
| **Templates Index** | [index.md](./templates/index.md) | Categorized index of all 38 templates across AI, databases, web frameworks, and APIs |


---

## 6. Autonomous App Builder Platform (`vibesdk/`)

An open-source, agentic platform for building and deploying full-stack web applications on Cloudflare.

| Resource | Path | Description |
| :--- | :--- | :--- |
| **Overview & Capabilities** | [README.md](./vibesdk/README.md) | ThinkAgent loop, SpaceDO workspace, Dynamic Worker previews, and Facets |
| **Agent Guidelines** | [AGENTS.md](./vibesdk/AGENTS.md) | Operational boundaries, tool access rules, and coding assistant instructions |
| **Documentation Index** | [index.md](./vibesdk/index.md) | Index of architecture diagrams, setup guides, LLM prompt engineering, and skills |


---

## 7. Next.js on Vite Framework (`vinext/`)

Running Next.js applications (App Router, Pages Router, RSC, Server Actions) on Vite for Cloudflare Workers.

| Resource | Path | Description |
| :--- | :--- | :--- |
| **Overview & Status** | [README.md](./vinext/README.md) | Feature status, App/Pages router support, quickstart, C3 setup, and known gaps |
| **Agent Guidelines** | [AGENTS.md](./vinext/AGENTS.md) | Complete development principles, architecture, RSC/Server Action pipelines, and test suites |
| **Framework Index** | [index.md](./vinext/index.md) | Index of migration skills, compatibility matrices, and production config examples |
| **Migration Skill** | `skills/` | [migrate-to-vinext](./vinext/skills/migrate-to-vinext/SKILL.md) automated migration workflow |

---

## 8. Core Developer Toolchain (`worker-sdk/`)

Cloudflare''s official developer toolchain monorepo: Wrangler CLI, Miniflare, C3, and Vite/Vitest plugins.

| Resource | Path | Description |
| :--- | :--- | :--- |
| **Overview & Quickstart** | [README.md](./worker-sdk/README.md) | Quickstart with C3 (`create-cloudflare`), official documentation links, and resources |
| **Agent Guidelines** | [AGENTS.md](./worker-sdk/AGENTS.md) | High-frequency commands, repository boundaries, Turborepo rules, and AI guidelines |
| **Toolchain Index** | [index.md](./worker-sdk/index.md) | Package topology (`wrangler`, `miniflare`, `c3`, plugins) and Turborepo workflows |
| **Engineering Skill** | `skills/` | [workers-sdk Skill](./worker-sdk/skills/workers-sdk/SKILL.md) development and testing manual |
