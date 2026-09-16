# OpenAI Agents SDK Integration Index

Index of reference guides and implementation patterns for running `@openai/agents` inside Cloudflare Agents.

## Core Documents

| Document | Type | Description |
| --- | --- | --- |
| [AGENTS.md](./AGENTS.md) | Technical Guide | Architectural composition, streaming patterns, handoffs, and Workers AI integration |
| [README.md](./README.md) | Overview | Introduction, benefits of edge hosting, and setup instructions |

---

## Reference Implementations

| Implementation | Scope | Key Concepts Demonstrated |
| --- | --- | --- |
| [basic](./doc/basic.md) | Minimal Starter | Wrapping an OpenAI agent inside a Cloudflare Durable Object `CFAgent` |
| [call-my-agent](./doc/call-my-agent.md) | Voice / Telephony | Twilio integration enabling phone calls directly into an OpenAI Agent |
| [chess-app](./doc/chess-app.md) | Stateful Games | Turn-based board game logic and state persistence with OpenAI Agents |
| [handoffs](./doc/handoffs.md) | Multi-Agent Orchestration | Routing queries between specialized domain tutor agents via a triage agent |
| [human-in-the-loop](./doc/human-in-the-loop.md) | Approval Workflows | Intercepting sensitive tool execution to require real-time human authorization |
| [llm-as-a-judge](./doc/llm-as-a-judge.md) | Evaluation | Using secondary evaluator agents to score and validate primary agent outputs |
| [pizzaz](./doc/pizzaz.md) | Interactive UI | Rich UI generation and generative web controls driven by agents |
| [streaming-chat](./doc/streaming-chat.md) | Real-time Streaming | Token-by-token streaming, tool call deltas, and stateful React chat UI |
