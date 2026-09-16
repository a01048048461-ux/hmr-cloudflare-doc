# Documentation Master Index

Comprehensive topic index for all guides, references, and how-tos in the Cloudflare Agents SDK documentation.

## Core Navigation

| Document | Type | Scope |
| --- | --- | --- |
| [AGENTS.md](./AGENTS.md) | Agent Guidelines | Diátaxis principles, authoring rules, Cloudflare style guide, and documentation sync |
| [README.md](./README.md) | Overview | Module structure, Diátaxis quadrant mapping, and general intro |

---

## 1. Core Agents SDK (`agents-docs/`)

| Topic | Category | Description |
| --- | --- | --- |
| [Getting Started](./agents-docs/getting-started.md) | Tutorial | Onboarding guide and creating your first Cloudflare Agent |
| [Adding to Existing Project](./agents-docs/adding-to-existing-project.md) | How-To | Integrating Agents SDK into an existing Cloudflare Worker |
| [Agent Class](./agents-docs/agent-class.md) | Reference | Core `Agent<Env, State>` API, methods, and lifecycle handlers |
| [Callable Methods](./agents-docs/callable-methods.md) | Reference | `@callable()` decorator, RPC, streaming responses, and client invocation |
| [State Management](./agents-docs/state.md) | Reference | Strongly-typed SQLite-backed state synchronization and transactions |
| [Configuration](./agents-docs/configuration.md) | Reference | `wrangler.jsonc` configuration, compatibility flags, and bindings |
| [HTTP & WebSockets](./agents-docs/http-websockets.md) | How-To | Real-time dual-transport routing, client connections, and events |
| [Routing](./agents-docs/routing.md) | How-To | `routeAgentRequest`, multi-agent URL patterns, and sub-agent routing |
| [Sub-Agents](./agents-docs/sub-agents.md) | How-To | Multi-agent architectures, child facets, and hierarchical delegation |
| [Agent Tools](./agents-docs/agent-tools.md) | How-To | Wrapping agents as callable LLM tools and orchestrating runs |
| [Chat Agents](./agents-docs/chat-agents.md) | Guide | High-level chat agents, streaming text, and AI SDK integration |
| [Chat SDK](./agents-docs/chat-sdk.md) | Reference | Lightweight chat helpers and abstractions |
| [Client SDK](./agents-docs/client-sdk.md) | Reference | `@cloudflare/agents/react`, `useAgent`, and client-side hooks |
| [Client Tools Continuation](./agents-docs/client-tools-continuation.md) | How-To | Resuming agent execution after client-side tool completion |
| [Human in the Loop](./agents-docs/human-in-the-loop.md) | How-To | Pausing execution for human approval before critical actions |
| [Scheduling & Tasks](./agents-docs/scheduling.md) | Reference | Durable alarms, cron jobs, and scheduled agent invocations |
| [Durable Execution](./agents-docs/durable-execution.md) | How-To | Long-running tasks, surviving worker evictions, and checkpointing |
| [Observability](./agents-docs/observability.md) | How-To | Logging, tracing, OpenTelemetry, and agent performance monitoring |
| [Readonly Connections](./agents-docs/readonly-connections.md) | How-To | Enforcing read-only access for untrusted clients or viewers |
| [Resumable Streaming](./agents-docs/resumable-streaming.md) | How-To | SSE streaming that seamlessly reconnects and catches up |
| [Retries](./agents-docs/retries.md) | How-To | Configurable retry strategies, jitter, and exponential backoff |
| [Push Notifications](./agents-docs/push-notifications.md) | How-To | Sending web push notifications from agents |
| [Email Routing](./agents-docs/email.md) | How-To | Receiving, parsing, and sending emails directly from agents |
| [Webhooks](./agents-docs/webhooks.md) | How-To | Receiving webhooks (GitHub, Stripe, etc.) into persistent agents |
| [Workflows](./agents-docs/workflows.md) | How-To | Orchestrating Cloudflare Workflows from agent instances |
| [Browse the Web](./agents-docs/browse-the-web.md) | How-To | Autonomous web browsing with Cloudflare Browser Rendering |
| [MCP Client](./agents-docs/mcp-client.md) | How-To | Connecting agents to external Model Context Protocol servers |
| [MCP Servers](./agents-docs/mcp-servers.md) | How-To | Hosting MCP servers on Cloudflare Workers |
| [MCP Transports](./agents-docs/mcp-transports.md) | Reference | SSE, Stream, and HTTP transports for MCP |
| [Securing MCP Servers](./agents-docs/securing-mcp-servers.md) | How-To | Authentication and authorization for MCP endpoints |
| [Cross-Domain Auth](./agents-docs/cross-domain-authentication.md) | How-To | Securing cross-origin WebSocket and HTTP agent sessions |
| [AI SDK v5 Migration](./agents-docs/migration-to-ai-sdk-v5.md) | Guide | Upgrading from Vercel AI SDK v4 to v5 |
| [AI SDK v6 Migration](./agents-docs/migration-to-ai-sdk-v6.md) | Guide | Upgrading to Vercel AI SDK v6 |

---

## 2. Code-Mode & Sandboxed Execution (`codemode/`)

| Topic | Description |
| --- | --- |
| [Codemode Overview](./codemode/index.md) | Architecture and concept of LLMs writing and executing code tools |
| [Runtime](./codemode/runtime.md) | Isolated TypeScript execution environment inside Cloudflare Workers |
| [Connectors](./codemode/connectors.md) | Connecting codemode isolates to external APIs, databases, and services |
| [Approvals](./codemode/approvals.md) | Policy-based execution approval workflows |
| [Snippets](./codemode/snippets.md) | Reusable tool functions and code generation patterns |
| [Vite Plugin](./codemode/vite-plugin.md) | Bundling and transforming codemode modules during development |

---

## 3. Virtual Workspace & Shell (`shell/`)

| Topic | Description |
| --- | --- |
| [Workspace & Shell Index](./shell/index.md) | Virtual SQLite+R2 filesystem, bash runner, and container execution |

---

## 4. Think Agent Framework (`think/`)

| Topic | Description |
| --- | --- |
| [Think Master Index](./think/index.md) | Comprehensive overview of `@cloudflare/think` |
| [Getting Started](./think/getting-started.md) | Quickstart tutorial for building Think agents |
| [Lifecycle Hooks](./think/lifecycle-hooks.md) | Full guide to turn cycles, hooks, and capability extensions |
| [Actions](./think/actions.md) | Defining, executing, and intercepting agent actions |
| [Tools](./think/tools.md) | Tool registration, execution ladders, and dynamic schemas |
| [Client Tools](./think/client-tools.md) | Interacting with the browser and delegating tools to the client |
| [Channels](./think/channels.md) | Real-time multi-channel communication |
| [Messengers](./think/messengers.md) | Message transformation, formatting, and delivery adapters |
| [Programmatic Submissions](./think/programmatic-submissions.md) | Background, webhook, and API submissions into think sessions |
| [Sub-Agents in Think](./think/sub-agents.md) | Hierarchical think agents and swarm orchestration |
| [Workflows in Think](./think/workflows.md) | Durable multi-step workflow integration |

---

## 5. Realtime Voice (`voice/`)

| Topic | Description |
| --- | --- |
| [Voice Index](./voice/index.md) | Realtime voice agent concepts, WebRTC/WebSocket audio streaming, and provider integration |
