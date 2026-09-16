# Cloudflare Sandbox SDK Documentation Index

Index of all documentation, architecture guides, Docker specifications, and skills for the **Cloudflare Sandbox SDK** (`@cloudflare/sandbox`).

## Core Documents

| Document | Type | Description |
| --- | --- | --- |
| [AGENTS.md](./AGENTS.md) | Agent Guide | Architecture overview, monorepo commands, testing workflows, and AI guidelines |
| [README.md](./README.md) | Overview | Quickstart, installation, Dockerfile configuration, and basic Worker usage |


---

## Technical Documentation (`docs/`)

| Document | Area | Description |
| --- | --- | --- |
| [Architecture](./docs/ARCHITECTURE.md) | Architecture | Three-layer model, Worker-to-container communication, and protocol overview |
| [Session Execution](./docs/SESSION_EXECUTION.md) | Execution | Running commands, managing interactive terminal sessions, and streams |
| [Session Execution Deep Dive](./docs/SESSION_EXECUTION_DEEP_DIVE.md) | Internals | Low-level execution engine, WebSocket multiplexing, and lifecycle management |
| [Concurrency](./docs/CONCURRENCY.md) | Scalability | Handling concurrent container instances, queuing, and pool limits |
| [Error Handling](./docs/ERROR_HANDLING.md) | Reliability | Error codes, timeout recovery, network disconnection, and failure modes |
| [Jupyter Notebooks](./docs/JUPYTER_NOTEBOOKS.md) | Python / Data | Running headless Jupyter kernels and evaluating code cells |
| [OpenAI Agents Integration](./docs/OPENAI_AGENTS.md) | AI Agents | Connecting OpenAI Agents to Sandbox execution tools (code-interpreter) |
| [Standalone Binary](./docs/STANDALONE_BINARY.md) | Container Server | Lightweight container-internal HTTP/WebSocket server daemon |
| [E2E Testing](./docs/E2E_TESTING.md) | Testing | Integration testing strategies with live containers |
| [Performance Testing](./docs/PERF_TESTING.md) | Testing | Benchmarking execution latency, cold starts, and throughput |
| [CI Pipeline](./docs/CI.md) | DevOps | GitHub Actions CI/CD workflows, image builds, and automated tests |
| [Release Process](./docs/RELEASE.md) | DevOps | Versioning, changesets, and npm/Docker release protocol |

---

## Engineering Skills (`skills/`)

| Skill | Description |
| --- | --- |
| [architecture](./skills/architecture/SKILL.md) | Three-layer architecture, client/server boundaries, and monorepo structure |
| [session-execution](./skills/session-execution/SKILL.md) | Best practices for executing shell commands and parsing container streams |
| [sandbox-bridge](./skills/sandbox-bridge/SKILL.md) | Worker-to-container RPC bridge and communication protocols |
| [testing](./skills/testing/SKILL.md) | Writing and running unit, integration, and browser E2E tests |
| [logging](./skills/logging/SKILL.md) | Structured logging conventions across SDK and container runtimes |
| [coding-standards](./skills/coding-standards/SKILL.md) | TypeScript, Biome, and code quality standards |
| [changesets](./skills/changesets/SKILL.md) | Generating changesets for versioned package releases |
| [examples](./skills/examples/SKILL.md) | Scaffolding and maintaining runnable sandbox demo applications |
| [git-commit](./skills/git-commit/SKILL.md) | Git commit conventions and semantic message formatting |
