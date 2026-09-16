# Cloudflare Agents SDK Documentation

Welcome to the documentation for the Cloudflare Agents SDK. This folder contains developer guides, tutorials, how-tos, and API reference documentation organized across the core SDK modules.

## Documentation Structure

Our documentation follows the **Diátaxis** framework:
- **Tutorials**: Step-by-step onboarding and end-to-end learning guides.
- **How-To Guides**: Practical recipes for solving specific engineering challenges (e.g. human-in-the-loop, MCP integration, email routing).
- **Reference**: In-depth API details, configuration options, method signatures, and parameter specifications.

*(For architectural rationale, design decisions, and RFCs, see the `design/` folder).*

## Modules Overview

- **[agents-docs/](./agents-docs/)**: Core framework docs covering `Agent`, state management, HTTP/WebSocket routing, Durable Objects, scheduling, MCP servers/clients, and sub-agents.
- **[codemode/](./codemode/)**: Secure code-mode runtime, dynamic tool execution, connectors, and execution approvals.
- **[shell/](./shell/)**: Container and virtual workspace filesystem (hybrid SQLite+R2) with command execution capabilities.
- **[think/](./think/)**: The `@cloudflare/think` framework for autonomous, turn-based, multi-step thinking agents with lifecycle hooks and messengers.
- **[voice/](./voice/)**: Low-latency realtime voice agent capabilities.

See [index.md](./index.md) for the complete directory of topics and guides.
