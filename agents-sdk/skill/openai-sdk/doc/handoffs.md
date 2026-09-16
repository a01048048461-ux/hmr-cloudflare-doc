# OpenAI Agents Handoffs on Cloudflare

Demonstrates multi-agent orchestration and dynamic agent delegation (handoffs) using `@openai/agents` inside Cloudflare Agents (`@cloudflare/agents`).

## Overview

In multi-agent architectures, handoffs allow an agent to transfer control of a conversation or query to another specialized agent. This example shows how a triage agent evaluates incoming questions and routes them to dedicated domain tutors.

## Architecture & Agents

- **History Tutor (`historyTutorAgent`)**: Specialized in answering history-related questions, explaining context and historical events.
- **Math Tutor (`mathTutorAgent`)**: Specialized in solving math problems with step-by-step reasoning and examples.
- **Triage Agent (`triageAgent`)**: Configured with `handoffs: [historyTutorAgent, mathTutorAgent]` to assess queries and delegate execution.
- **Cloudflare Agent Integration**: Wrapped in `MyAgent extends CFAgent`, making the multi-agent system stateful and deployable as a Cloudflare Worker / Durable Object.

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
