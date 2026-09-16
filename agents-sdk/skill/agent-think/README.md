# agent-think

`agent-think` is an autonomous engineering agent built on `@cloudflare/think` and `@cloudflare/workspace` designed to triage, reproduce, and fix GitHub issues on `cloudflare/agents`.

## Overview

Unlike traditional CI runners, `agent-think` runs inside a persistent Cloudflare Worker backed by a warm Linux container sandbox. Triggered via issue comments (e.g. `@agent-think reproduce this issue` or `@agent-think open a PR fixing this`), the agent operates autonomously as the **agent-think GitHub App** without impersonating human users.

## System Topology

- **GitHub App Hook (`gh-app`)**: Handles webhook signatures, member verification, token minting, and dispatches turns.
- **Worker Entrypoint (`AgentThink`)**: Submits durable turns into `ThinkAgent` sessions in ~1 second.
- **`ThinkAgent` (Durable Object)**: Owns durable turns, conversation state, and execution history.
- **`WorkspaceAgent` (Durable Object)**: Manages the virtual file system (VFS) and container bridge.
- **`Sandbox` & `WarmPool`**: Manages container lifecycles and keeps a warm container ready for instantaneous turn execution.
- **Command Center UI**: Real-time management interface, live thread viewer, and operator controls.

## Core Capabilities & Guides

- **Bug Reproduction (`docs/reproduce.md`)**: Analyzes issues, scaffolds an isolated 7-file project with a Vite+React UI, deploys to a temporary preview account, verifies the bug live, pushes an orphan `repro/issue-<id>` branch, and comments on the issue.
- **Automated Fix PR (`docs/open-pr.md`)**: Identifies the root cause, writes a minimal fix with regression tests and changesets, packs the package, deploys a live temporary demo, and submits a linked PR.

## Documentation Index

See [index.md](./index.md) for the complete catalogue of documentation and implementation guides.
