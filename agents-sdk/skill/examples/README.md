# Cloudflare Agents SDK Examples

A collection of 55 self-contained, runnable example applications demonstrating how to build with the Cloudflare Agents SDK.

## Purpose & Philosophy

Each example in this catalogue is focused on demonstrating **one primary feature or concept** (such as Model Context Protocol, WebSocket streaming, voice integration, or durable recovery).

Most examples are full-stack projects featuring:
- A Cloudflare Worker backend powered by SQLite-backed Durable Objects.
- A client frontend built with Vite, React, and `@cloudflare/agents/react` (`useAgent`).
- Transparent, observable logs and interactive controls to trigger agent actions.

*(The exception is `playground/`, which is an expansive kitchen-sink showcase combining multiple capabilities).*

## How to Run Examples

Each example project follows standard Cloudflare Workers conventions:

1. **Navigate to the example directory**
2. **Install dependencies**:
   ```bash
   pnpm install
   ```
3. **Configure environment variables**:
   ```bash
   cp .env.example .env
   # Add necessary API keys (OpenAI, Anthropic, ElevenLabs, etc.)
   ```
4. **Start local development**:
   ```bash
   pnpm run start # or pnpm run dev
   ```

## Catalogue Index

Browse [index.md](./index.md) for the complete categorized list of all 55 examples.
