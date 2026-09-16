# Cloudflare Agents SDK Packages

This directory contains the foundational packages that comprise the Cloudflare Agents SDK monorepo.

## Package Suite Overview

- **[@cloudflare/agents](./doc/agents.md)**: The core foundational SDK providing `Agent`, `routeAgentRequest`, `@callable()`, SQLite-backed state management, and real-time WebSocket connectivity.
- **[@cloudflare/ai-chat](./doc/ai-chat.md)**: High-level chat primitives, conversational memory, streaming, and tool execution.
- **[@cloudflare/codemode](./doc/codemode.md)**: Secure in-worker code execution runtime and dynamic tool generation.
- **[@cloudflare/hono-agents](./doc/hono-agents.md)**: First-class adapters and routing middleware for Hono applications.
- **[@cloudflare/shell](./doc/shell.md)**: Hybrid SQLite+R2 virtual filesystem, command runner, and workspace environment.
- **[@cloudflare/think](./doc/think.md)**: Advanced autonomous agent framework featuring durable turns, lifecycle hooks, and multi-channel messengers.
- **[@cloudflare/voice](./doc/voice.md)**: Low-latency realtime voice agent capabilities supporting WebRTC and WebSocket audio streaming.
- **[@cloudflare/worker-bundler](./doc/worker-bundler.md)**: High-performance runtime bundling utility for Cloudflare Workers.

## Monorepo Management

- **Package Manager**: `pnpm` (version 9+)
- **Monorepo Engine**: `Nx`
- **Build System**: `tsup` / `oxc`
- **Linter & Formatter**: `oxlint` / `oxfmt`

See [index.md](./index.md) for detailed package specifications.
