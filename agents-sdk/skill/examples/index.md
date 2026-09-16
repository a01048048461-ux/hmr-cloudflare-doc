# Examples Master Index

Categorized index of all 55 reference applications in the Cloudflare Agents SDK examples library.

## Core Documents

| Document | Description |
| --- | --- |
| [AGENTS.md](./AGENTS.md) | Authoring guidelines, required structure, and standards for AI agents |
| [README.md](./README.md) | Overview of example architecture and local execution instructions |
| [TODO.md](./TODO.md) | Planned examples and backlog items |

---

## 1. Core Framework & State Primitives

| Example | Description |
| --- | --- |
| [a2a](./docs/a2a.md) | Agent-to-Agent direct RPC communication |
| [agent-skills](./docs/agent-skills.md) | Composable capabilities and skills integration |
| [agents-as-tools](./docs/agents-as-tools.md) | Packaging sub-agents as callable LLM tools |
| [auth-agent](./docs/auth-agent.md) | Authentication and session token validation |
| [cross-domain](./docs/cross-domain.md) | Cross-origin WebSocket and HTTP agent connectivity |
| [dynamic-tools](./docs/dynamic-tools.md) | Registering and updating tools at runtime |
| [dynamic-workers](./docs/dynamic-workers.md) | Dynamically spawning worker instances |
| [dynamic-workers-playground](./docs/dynamic-workers-playground.md) | Interactive sandbox for testing dynamic worker pools |
| [playground](./docs/playground.md) | Kitchen-sink showcase demonstrating the full range of SDK features |
| [push-notifications](./docs/push-notifications.md) | Delivering web push notifications from agents |
| [structured-input](./docs/structured-input.md) | Type-safe JSON schemas and input validation |

---

## 2. Chat & Conversational Interfaces

| Example | Description |
| --- | --- |
| [ai-chat](./docs/ai-chat.md) | Basic AI chat agent with streaming responses |
| [assistant](./docs/assistant.md) | Full-featured conversational assistant with tools and state |
| [chat-sdk-messenger](./docs/chat-sdk-messenger.md) | Chat SDK messenger adapters and UI components |
| [context-overflow-recovery](./docs/context-overflow-recovery.md) | Managing context limits with automatic summarization |
| [multi-ai-chat](./docs/multi-ai-chat.md) | Multi-participant group chat with AI agents |
| [resumable-stream-chat](./docs/resumable-stream-chat.md) | Reconnectable streaming chat sessions |
| [vue-chat](./docs/vue-chat.md) | Full-stack chat agent implemented with Vue.js frontend |
| [workspace-chat](./docs/workspace-chat.md) | Chat agent integrated with workspace files |

---

## 3. Model Context Protocol (MCP)

| Example | Description |
| --- | --- |
| [mcp](./docs/mcp.md) | Minimal MCP server on Cloudflare Workers |
| [mcp-client](./docs/mcp-client.md) | Agent acting as an MCP client querying external tools |
| [mcp-elicitation](./docs/mcp-elicitation.md) | Interactive parameter elicitation in MCP |
| [mcp-elicitation-mrtr](./docs/mcp-elicitation-mrtr.md) | Multi-round tool parameter elicitation |
| [mcp-rpc-transport](./docs/mcp-rpc-transport.md) | Low-level RPC transport implementation for MCP |
| [mcp-server](./docs/mcp-server.md) | Dedicated standalone MCP server deployment |
| [mcp-worker](./docs/mcp-worker.md) | Standard MCP server running inside Cloudflare Workers |
| [mcp-worker-authenticated](./docs/mcp-worker-authenticated.md) | Authenticated and secured MCP server endpoints |
| [webmcp](./docs/webmcp.md) | Exposing MCP tools to browser extensions and native web APIs |
| [webmcp-react](./docs/webmcp-react.md) | React components interacting with WebMCP tools |

---

## 4. Code-Mode & Sandboxing

| Example | Description |
| --- | --- |
| [codemode](./docs/codemode.md) | Core code-mode architecture: agents generating and running code |
| [codemode-browser](./docs/codemode-browser.md) | Code-mode driving browser rendering and automation |
| [codemode-connectors](./docs/codemode-connectors.md) | Connecting dynamic code isolates to third-party APIs |
| [codemode-mcp](./docs/codemode-mcp.md) | Generating code that executes MCP client tools |
| [codemode-mcp-openapi](./docs/codemode-mcp-openapi.md) | Auto-generating code tools from OpenAPI specifications |
| [sandbox-coding-agent](./docs/sandbox-coding-agent.md) | Autonomous software engineering agent in an isolated workspace |

---

## 5. Voice & Audio Agents

| Example | Description |
| --- | --- |
| [voice-agent](./docs/voice-agent.md) | Low-latency full-duplex realtime voice agent |
| [voice-input](./docs/voice-input.md) | Speech-to-text audio input handling |
| [elevenlabs-starter](./docs/elevenlabs-starter.md) | Realtime conversational voice using ElevenLabs |
| [plivo-voice-agent](./docs/plivo-voice-agent.md) | Telephony voice agent connected via Plivo |
| [telnyx-voice-agent](./docs/telnyx-voice-agent.md) | Telephony voice agent connected via Telnyx |

---

## 6. Workflows & Durable Execution

| Example | Description |
| --- | --- |
| [workflows](./docs/workflows.md) | Orchestrating Cloudflare Workflows from agents |
| [deploy-churn](./docs/deploy-churn.md) | Stress-testing agent durability across rolling deploys |
| [worker-bundler-playground](./docs/worker-bundler-playground.md) | Runtime asset bundling without precompilation |

---

## 7. Webhooks, External Services & Specialized

| Example | Description |
| --- | --- |
| [browser-live-view](./docs/browser-live-view.md) | Live visual streaming of headless browser sessions |
| [browser-quick-actions](./docs/browser-quick-actions.md) | Automated web actions and form interactions |
| [channels](./docs/channels.md) | Multi-channel messaging and broadcast patterns |
| [email-agent](./docs/email-agent.md) | Autonomous email receiving, parsing, and reply agent |
| [github-webhook](./docs/github-webhook.md) | Processing GitHub issue and commit webhooks |
| [next](./docs/next.md) | Early-access staging ground for next-generation SDK features |
| [tictactoe](./docs/tictactoe.md) | Interactive multiplayer stateful board game |
| [x402](./docs/x402.md) | Micro-payments and paid agent tool calls via HTTP 402 |
| [x402-mcp](./docs/x402-mcp.md) | Paid MCP tool execution with Lightning/crypto payment gateways |

---

## 8. Think Framework Examples

| Example | Description |
| --- | --- |
| [think-chat-sdk](./docs/think-chat-sdk.md) | Integrating `@cloudflare/think` with frontend chat components |
| [think-submissions](./docs/think-submissions.md) | Programmatic background turns and submissions into Think |
| [think-workflows](./docs/think-workflows.md) | Combining Think autonomous agents with Cloudflare Workflows |
