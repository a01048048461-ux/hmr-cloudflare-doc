# Experimental Modules Index

Directory index of all research spikes, prototypes, and experimental capabilities in the Cloudflare Agents SDK.

## Core Documents

| Document | Type | Description |
| --- | --- | --- |
| [AGENTS.md](./AGENTS.md) | Guidelines | Scope, stability boundaries, and engineering conventions for experimental work |
| [README.md](./README.md) | Overview | High-level summary of experimental initiatives and unstable API warnings |

---

## 1. Chat Recovery & Fault Tolerance

| Document | Description |
| --- | --- |
| [chat-recovery-probe](./docs/chat-recovery-probe.md) | Active probing and verification of chat state recovery under simulated crash conditions |
| [forever-chat](./docs/forever-chat.md) | Multi-provider conversation recovery across OpenAI, Anthropic, and Workers AI |
| [pi-recovery](./docs/pi-recovery.md) | State recovery patterns specifically tailored for Pi agent architectures |
| [tanstack-recovery](./docs/tanstack-recovery.md) | State synchronization and recovery integrated with TanStack Query and Router |

---

## 2. Durable Execution & Fibers

| Document | Description |
| --- | --- |
| [forever-fibers](./docs/forever-fibers.md) | Durable background worker fibers with progress reporting and eviction survival |
| [inference-buffer](./docs/inference-buffer.md) | In-memory and persistent stream buffering for interrupted LLM generations |
| [gateway-resume](./docs/gateway-resume.md) | Pausing, checkpointing, and resuming inference streams via Cloudflare AI Gateway |
| [gateway-resume-think](./docs/gateway-resume-think.md) | Integrating AI Gateway resumption with Think turn execution |

---

## 3. Sandboxing, Isolation & "Gadgets"

| Document | Description |
| --- | --- |
| [gadgets-chat](./docs/gadgets-chat.md) | Structural multi-room chat isolation using Durable Object facets |
| [gadgets-gatekeeper](./docs/gadgets-gatekeeper.md) | Architectural Gatekeeper pattern for intercepting and approving sensitive tool calls |
| [gadgets-sandbox](./docs/gadgets-sandbox.md) | Worker Loader sandboxing for executing untrusted guest code inside Workers |
| [gadgets-subagents](./docs/gadgets-subagents.md) | Facet-backed sub-agent hierarchy and lifecycle isolation |
| [ops-approval-agent](./docs/ops-approval-agent.md) | Dedicated human-in-the-loop operational approval queue agent |
