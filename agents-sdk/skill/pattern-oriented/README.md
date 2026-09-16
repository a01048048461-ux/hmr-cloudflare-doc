# Pattern-Oriented Agent Guides

In-depth, pattern-oriented tutorials and architectural walkthroughs demonstrating how to build robust, multi-faceted AI agent systems using the Cloudflare Agents SDK.

## How Guides Differ from Examples

- **Examples (`examples/`)**: Short, focused demo applications showcasing **a single feature or concept** (e.g. basic MCP server, simple chat streaming).
- **Guides (`pattern-oriented/`)**: End-to-end architectural tutorials teaching **a holistic workflow or design pattern** spanning multiple subsystems, complete with narrative explanations of tradeoffs, design decisions, and production best practices.

## Core Architectural Patterns

- **[Anthropic Agentic Patterns](./docs/anthropic-patterns.md)**: Implementation of the five canonical agentic workflows from Anthropic's research:
  1. Prompt Chaining (Sequential decomposition)
  2. Routing (Classifying and dispatching)
  3. Parallelization (Concurrent sectioning and voting)
  4. Orchestrator-Workers (Dynamic delegation and synthesis)
  5. Evaluator-Optimizer (Iterative refinement loops)
- **[Human-in-the-Loop Architecture](./docs/human-in-the-loop.md)**: Design and implementation of agents that safely delegate sensitive actions to human operators for interactive real-time approval.

See [index.md](./index.md) for the guide catalogue and links.
