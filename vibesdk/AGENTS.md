# VibeSDK — Project Rules

This repository contains VibeSDK, a Cloudflare platform for vibe-coded applications and autonomous AI agents (ThinkAgent, SpaceDO). Detailed architecture guides and change paths are located in the **`vibesdk` skill** at [`.agents/skills/vibesdk/SKILL.md`](SKILL.md).

---

## High-Frequency Commands (Bun)

* **Dev**: `bun run dev` (starts React app + Worker at `http://localhost:5173`)
* **Checks**: `bun run typecheck`, `bun run lint`, `bun run test`, `bun run build`
* **Database**: `bun run db:generate` && `bun run db:migrate:local`
* **Types**: `bun run cf-typegen`

---

## Core Guidelines

* **Frontend**: React + Tailwind v4 (`src/index.css`) + `@cloudflare/kumo`. Server state strictly in TanStack Query (`src/lib/query-keys.ts`).
* **Backend**: Worker + Durable Objects (`worker/index.ts`, `worker/app.ts`).
* **Space Package**: `SpaceDO` provides durable filesystem & git history over Cloudflare Artifacts. Edit `space/src/`, never `space/dist/`.
* **SDK Package**: Independent package in `sdk/`. Changes to WebSocket protocol (`worker/api/websocketTypes.ts`) must maintain backward compatibility.

---

## Boundaries

* **Never**: Commit `.dev.vars*`, `.prod.vars`, or Cloudflare API tokens.
* **Never**: Introduce new `any` types.
* **Always**: Use Bun and respect owner-only route protections.

> For complete workflows, see [`.agents/skills/vibesdk/SKILL.md`](SKILL.md).
