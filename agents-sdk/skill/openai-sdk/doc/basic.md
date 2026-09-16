# Basic OpenAI Cloudflare Agent

A minimal starter example integrating the `@openai/agents` SDK with Cloudflare Agents (`@cloudflare/agents`).

## Overview

This template shows how to host an OpenAI Agent within a Cloudflare Worker Durable Object using the Cloudflare Agents SDK.

## How It Works

- **Agent Definition**: In `src/server.ts`, `MyAgent` extends `CFAgent<Env>` from `agents`.
- **OpenAI Agent Setup**: Instantiates `new Agent({ instructions, name })` from `@openai/agents`.
- **Execution**: Uses `run(agent, prompt)` to execute the agent on incoming HTTP requests.
- **Routing**: `routeAgentRequest(request, env)` maps incoming requests to the appropriate agent instance.
- **Workers AI Provider**: Includes commented configuration for optionally running models on Cloudflare Workers AI (`workers-ai-provider` and `@cf/moonshotai/kimi-k2.7-code`).

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
