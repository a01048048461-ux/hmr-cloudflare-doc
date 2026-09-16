# Streaming Chat with OpenAI Agents & Cloudflare

An interactive real-time streaming chat application integrating `@openai/agents` with Cloudflare Agents (`@callable({ streaming: true })`).

## Features

- **Real-Time Token Streaming**: Streams text tokens (`output_text_delta`) chunk-by-chunk to the frontend via `StreamingResponse`.
- **Tool Calling & Execution Events**: Emits typed stream chunks for tool calls (`tool-call`) and results (`tool-result`), featuring a mock weather tool (`getWeather`).
- **Stateful History**: Retains chat history in `AgentState.messages` across the Durable Object lifecycle.
- **Modern React Frontend**: Clean UI using `@cloudflare/agents/react` with `useAgent` to consume streaming chunks (`onChunk`, `onDone`).

## How It Works

1. **Client Invocation**: Client calls `agent.call("chat", [message], { stream: { onChunk, onDone } })`.
2. **Streaming Endpoint**: On the server, `MyAgent.chat(stream: StreamingResponse, userMessage: string)` initiates a streamed run:
   ```ts
   const result = await run(agent, messages, { stream: true });
   ```
3. **Chunk Forwarding**: Iterates over events in `result`, sending typed chunks (`text-delta`, `tool-call`, `tool-result`) via `stream.send()`.
4. **Completion**: Calls `stream.end()` upon completion, updating conversation state.

## Getting Started

### Prerequisites

- Node.js 18+
- pnpm
- OpenAI API key

### Setup

1. **Install dependencies**:
   ```bash
   pnpm install
   ```

2. **Configure environment**:
   ```bash
   cp .env.example .env
   ```
   Add your `OPENAI_API_KEY` to `.env`.

3. **Start development server**:
   ```bash
   pnpm start
   ```
