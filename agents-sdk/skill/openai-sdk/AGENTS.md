# AGENTS.md — openai-sdk/

Architectural guide and developer rules for AI agents implementing the OpenAI Agents SDK (`@openai/agents`) on Cloudflare Agents.

## Composition Architecture

Running `@openai/agents` on Cloudflare Workers creates a complementary union of two complementary frameworks:
1. **OpenAI Agents SDK (`@openai/agents`)**: Provides reasoning loops, declarative tool binding, multi-agent handoffs, and agent evaluators.
2. **Cloudflare Agents SDK (`@cloudflare/agents`)**: Provides distributed stateful compute (Durable Objects), WebSocket connection management, SQLite persistence, alarms, and HTTP routing.

```
┌────────────────────────────────────────────────────────┐
│ Cloudflare Agent (CFAgent / Durable Object)           │
│  - routeAgentRequest / WebSocket Lifecycle             │
│  - Persistent SQLite State                             │
│  - Streaming RPC (@callable)                           │
│  ┌──────────────────────────────────────────────────┐  │
│  │ OpenAI Agent (Agent)                             │  │
│  │  - Instructions & Prompt Engineering             │  │
│  │  - Declarative Tools & Zod Schemas               │  │
│  │  - Multi-Agent Handoffs                          │  │
│  └──────────────────────────────────────────────────┘  │
└────────────────────────────────────────────────────────┘
```

## Key Patterns

### 1. Minimal Integration
Wrap OpenAI Agent execution within `CFAgent.onRequest()` or a `@callable()` method.
Always route incoming traffic in the Worker default export via `routeAgentRequest(request, env)`.

### 2. Streaming via `@callable({ streaming: true })`
When streaming token deltas and tool events:
- Receive `stream: StreamingResponse` on the server method.
- Pass `{ stream: true }` to `run(agent, history)`.
- Push typed chunks (`text-delta`, `tool-call`, `tool-result`) via `stream.send()`.
- Signal completion via `stream.end()`.

### 3. Agent Handoffs
Define specialized sub-agents (e.g. `historyTutor`, `mathTutor`) and supply them to a top-level `triageAgent` via the `handoffs: [...]` array.

### 4. Workers AI Provider Option
OpenAI Agents can be backed by Cloudflare Workers AI models using `workers-ai-provider` and `@openai/agents-extensions`, allowing local execution without external API dependencies.
