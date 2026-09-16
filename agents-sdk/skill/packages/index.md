# Monorepo Packages Index

Index and specifications for all core packages in the Cloudflare Agents SDK monorepo.

## Core Documents

| Document | Type | Description |
| --- | --- | --- |
| [AGENTS.md](./AGENTS.md) | Guidelines | Architecture graph, cross-package rules, testing policies, and Changesets |
| [README.md](./README.md) | Overview | High-level summary of the package suite and monorepo tooling |

---

## Published Packages

| Package Name | Documentation | Scope & Key Capabilities |
| --- | --- | --- |
| `@cloudflare/agents` | [doc/agents.md](./doc/agents.md) | Primary framework: `Agent<Env, State>`, SQLite persistence, `@callable()`, RPC, scheduling, WebSocket lifecycle |
| `@cloudflare/ai-chat` | [doc/ai-chat.md](./doc/ai-chat.md) | Conversational agents, multi-model streaming, conversation history, and tool integration |
| `@cloudflare/codemode` | [doc/codemode.md](./doc/codemode.md) | Sandboxed TypeScript runtime allowing agents to safely write and execute code tools |
| `@cloudflare/hono-agents` | [doc/hono-agents.md](./doc/hono-agents.md) | Hono middleware, sub-agent nested route handlers, and OpenAPI integration |
| `@cloudflare/shell` | [doc/shell.md](./doc/shell.md) | Virtual workspace filesystem combining SQLite metadata with R2 object storage |
| `@cloudflare/think` | [doc/think.md](./doc/think.md) | Autonomous agent execution engine with durable turns, lifecycle hooks, and messengers |
| `@cloudflare/voice` | [doc/voice.md](./doc/voice.md) | Realtime bi-directional audio streaming, VAD, and voice provider adapters |
| `@cloudflare/worker-bundler` | [doc/worker-bundler.md](./doc/worker-bundler.md) | Host-side module bundling and virtual worker packaging |
