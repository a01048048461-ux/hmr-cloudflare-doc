# Design Documentation Index

Index of all architectural design records, analyses, and Requests for Comments (RFCs) across the Cloudflare Agents SDK.

## Core Documents

| Document | Type | Scope |
| --- | --- | --- |
| [AGENTS.md](./AGENTS.md) | Guidelines | Philosophy of design records vs RFCs, Diátaxis explanation quadrant, and writing rules |
| [README.md](./README.md) | Overview | Rationale, purpose of design records, and guide to understanding SDK tradeoffs |

---

## 1. Core Architecture & Lifecycles

| Document | Type | Scope |
| --- | --- | --- |
| [docs/alarm-coordination.md](./docs/alarm-coordination.md) | Design Doc | Physical alarm coordination, capability contributions, and Scheduler adaptation |
| [docs/readonly-connections.md](./docs/readonly-connections.md) | Design Doc | Readonly connection enforcement, storage wrapping, and tradeoffs |
| [docs/retries.md](./docs/retries.md) | Design Doc | Retry primitives, integration points, and backoff strategy |
| [docs/test-coverage-matrix.md](./docs/test-coverage-matrix.md) | Analysis | Test layer coverage, CI mapping, and test hygiene |
| [docs/visuals.md](./docs/visuals.md) | Design Doc | UI component library (Kumo), dark mode, and UI patterns |
| [docs/rfc-durable-object-lifecycle.md](./docs/rfc-durable-object-lifecycle.md) | RFC | Durable Object lifecycle hooks and capability integration |

---

## 2. Think Agent & Chat Subsystems

| Document | Type | Scope |
| --- | --- | --- |
| [docs/think.md](./docs/think.md) | Design Doc | Think base class, sessions, streaming, tools, and execution ladder |
| [docs/think-vs-aichat.md](./docs/think-vs-aichat.md) | Analysis | Architectural comparison between Think and AIChatAgent |
| [docs/think-roadmap.md](./docs/think-roadmap.md) | Roadmap | Complete roadmap and AIChatAgent feature parity plan |
| [docs/think-durable-submissions.md](./docs/think-durable-submissions.md) | Design Doc | Programmatic async turns, recovery, and idempotency |
| [docs/think-execute-hitl.md](./docs/think-execute-hitl.md) | Design Doc | Human-in-the-loop tool execution within Think |
| [docs/chat-shared-layer.md](./docs/chat-shared-layer.md) | Design Doc | Shared protocol primitives, streaming, and sanitization |
| [docs/chat-api.md](./docs/chat-api.md) | Analysis | Pain points and improvements in AIChatAgent and useAgentChat |
| [docs/chat-improvements.md](./docs/chat-improvements.md) | Design Doc | Client DX items and shared chat extractions |
| [docs/rfc-chat-recovery-foundation.md](./docs/rfc-chat-recovery-foundation.md) | RFC | Resilient recovery engine and behavior convergence |
| [docs/rfc-chat-recovery-work-budget.md](./docs/rfc-chat-recovery-work-budget.md) | RFC | Work budget decoupling from runaway guards |
| [docs/rfc-think-actions.md](./docs/rfc-think-actions.md) | RFC | Structured action execution model |
| [docs/rfc-think-channels.md](./docs/rfc-think-channels.md) | RFC | Multi-channel communication abstractions |
| [docs/rfc-think-multi-session.md](./docs/rfc-think-multi-session.md) | RFC | Multi-session chat support via child facets |
| [docs/rfc-think-turns.md](./docs/rfc-think-turns.md) | RFC | Turn-based execution semantics |
| [docs/rfc-think-voice.md](./docs/rfc-think-voice.md) | RFC | Realtime voice integration into Think |
| [docs/rfc-user-chat-durable-objects.md](./docs/rfc-user-chat-durable-objects.md) | RFC | User hub topology with independent chat Durable Objects |

---

## 3. Sub-Agents, Tools & Orchestration

| Document | Type | Scope |
| --- | --- | --- |
| [docs/agent-tools.md](./docs/agent-tools.md) | Design Doc | Chat sub-agent orchestration, parent registry, and replay |
| [docs/sub-agent-routing.md](./docs/sub-agent-routing.md) | Design Doc | Facet-based child DO routing, nested URLs, and registry lookup |
| [docs/loopback.md](./docs/loopback.md) | Design Doc | Cross-boundary RPC for sub-agents and dynamic isolates |
| [docs/rfc-sub-agents.md](./docs/rfc-sub-agents.md) | RFC | Sub-agent architecture via facets and typed stubs |
| [docs/rfc-sub-agent-routing.md](./docs/rfc-sub-agent-routing.md) | RFC | External addressability and routing for sub-agents |
| [docs/rfc-helper-sub-agent-orchestration.md](./docs/rfc-helper-sub-agent-orchestration.md) | RFC | Agent tool orchestration (`runAgentTool`, `agentTool`) |
| [docs/rfc-detached-agent-tools.md](./docs/rfc-detached-agent-tools.md) | RFC | Detached background runs and completion hooks |

---

## 4. State, Storage, Filesystems & Providers

| Document | Type | Scope |
| --- | --- | --- |
| [docs/sessions.md](./docs/sessions.md) | Design Doc | Schema, write economics, and attachment maintenance |
| [docs/workspace.md](./docs/workspace.md) | Design Doc | Hybrid SQLite+R2 filesystem, bash runner, and observability |
| [docs/worker-bundler.md](./docs/worker-bundler.md) | Design Doc | Host-side asset bundling without code generation |
| [docs/voice.md](./docs/voice.md) | Design Doc | Voice providers architecture and audio stream handling |
| [docs/skills.md](./docs/skills.md) | Design Doc | Skill execution framework and agent extensibility |
| [docs/durable-streams-comparison.md](./docs/durable-streams-comparison.md) | Analysis | ElectricSQL Durable Streams vs Agents SDK comparison |
| [docs/rfc-fibers.md](./docs/rfc-fibers.md) | RFC | Resumable long-running fiber execution |
| [docs/rfc-sessions.md](./docs/rfc-sessions.md) | RFC | Persistent session primitives |
| [docs/rfc-streams.md](./docs/rfc-streams.md) | RFC | Resumable streaming protocol |
| [docs/rfc-workers-ai-gateway-merge.md](./docs/rfc-workers-ai-gateway-merge.md) | RFC | Unification of AI Gateway and Workers AI provider |
| [docs/rfc-codex-harness-capability.md](./docs/rfc-codex-harness-capability.md) | RFC | Codex Rust/Wasm engine capability |
| [docs/rfc-coding-agent.md](./docs/rfc-coding-agent.md) | RFC | Autonomous code modification and editing agent |
