# AGENTS.md — experimental/

Guidelines for AI agents working with or consulting the experimental capabilities within the Cloudflare Agents SDK.

## Purpose & Scope

This directory contains experimental prototypes, research spikes, and forward-looking capabilities that leverage unreleased or unstable Cloudflare Worker primitives (such as Durable Object Facets, Worker Loaders, Dynamic Isolate Sandboxes, and low-level resumption hooks).

> [!WARNING]
> Everything in `experimental/` is subject to breaking API changes or removal. Do not recommend these patterns for production workloads or stable customer integrations without explicit caveats.

## Core Themes

1. **Long-Running Execution & Fibers**: Background task execution that survives runtime restarts and memory evictions without blocking turns.
2. **Structural Isolation & Sandboxing ("Gadgets")**: Gatekeeper proxies, policy-enforced approval queues, and isolated worker environments.
3. **Chat Recovery & Fault Tolerance**: Resilient state restoration across diverse model providers (Workers AI, OpenAI, Anthropic).
4. **Gateway Resumption**: Buffered inference streams that can pause, resume, and hand off mid-generation.

## Conventions for Agents

- **Exploration vs. Stabilization**: Features here are validating patterns. When a pattern proves successful, it is codified into an RFC under `design/` and migrated to core packages (`packages/agents`, `packages/think`).
- **Dependency Isolation**: Experimental packages must not introduce non-optional peer dependencies to stable packages.
- **Documentation**: All experimental modules must clearly state prerequisites, required compatibility flags (e.g. `nodejs_compat`, experimental flags), and known limitations.
