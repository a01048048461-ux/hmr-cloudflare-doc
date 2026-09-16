# OpenAI Agents SDK on Cloudflare

This module provides reference guides and starter implementations demonstrating how to build and deploy applications using the official **OpenAI Agents SDK** (`@openai/agents`) on the **Cloudflare Agents SDK**.

## Why OpenAI Agents on Cloudflare?

- **Persistent Agent Memory**: Cloudflare Durable Objects give each agent instance its own dedicated SQLite database and persistent state.
- **Serverless Scale**: No servers to manage; instances scale to zero when idle and wake up instantly when messages arrive.
- **Real-time Dual-Transport**: Native WebSocket and HTTP support for instant interactive streaming and client-side tool execution.
- **Edge Deployment**: Runs close to users globally on Cloudflare's network.

## Prerequisites & Setup

1. **Prerequisites**: Node.js 18+, pnpm, and an OpenAI API key.
2. **Environment**: Add `OPENAI_API_KEY` to `.env`.
3. **Compatibility**: Ensure `compatibility_flags: ["nodejs_compat"]` is set in `wrangler.jsonc`.

## Reference Modules

Explore the complete list of 8 reference implementations in [index.md](./index.md).
