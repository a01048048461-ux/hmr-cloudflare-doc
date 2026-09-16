# Cloudflare OS Documentation Index

Index of all documentation, architectural specifications, guides, and skills for **Cloudflare OS: An AI Productivity Environment**.

## Core Documents

| Document | Type | Description |
| --- | --- | --- |
| [AGENTS.md](./AGENTS.md) | Agent Guidelines | Comprehensive system architecture, Durable Object topology, security, and developer instructions |
| [README.md](./README.md) | Overview | Introduction, quickstart (`pnpm run-local`), gadgets, blueprints, and Gatekeepers |

---

## Technical Documentation (`docs/`)

| Document | Area | Description |
| --- | --- | --- |
| [AI Gateway Billing](./docs/ai-gateway-billing.md) | Infrastructure | AI Gateway cost attribution, rate limits, and metering |
| [Blueprints](./docs/blueprints.md) | Application Engine | Pre-packaged application blueprints (slides, dashboards, chat, whiteboards) |
| [Connect Handoff](./docs/connect-handoff.md) | Connectivity | External tool connection and session handoff flows |
| [Integration Testing](./docs/integration-testing.md) | Quality Assurance | End-to-end testing strategies for agents and sandboxed gadgets |
| [OAuth Sign-In](./docs/oauth-signin.md) | Authentication | Identity management and enterprise OAuth authentication flows |
| [Observers](./docs/observers.md) | State & Reactive UI | Real-time observation, state change propagation, and UI synchronization |
| [Public Server](./docs/public-server.md) | Hosting | Public endpoint exposure and external API serving |
| [Sharing & Permissions](./docs/sharing.md) | Collaboration | Multi-tenant workspace sharing, access control, and collaboration rules |

---

## Skills (`skills/`)

| Skill | Description |
| --- | --- |
| [write-gatekeeper](./skills/write-gatekeeper/SKILL.md) | Authoring Gatekeepers: security policies, guardrails, and runtime execution filters for agents and gadgets |
| [write-gatekeeper Skeleton](./skills/write-gatekeeper/SKELETON.md) | Code template and skeleton for implementing custom Gatekeepers |
