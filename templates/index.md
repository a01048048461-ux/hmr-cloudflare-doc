# Cloudflare Workers Templates Index

Comprehensive index of all official starter templates for building full-stack applications, AI agents, databases, and microservices on Cloudflare Workers.

## Core Documents

| Document | Type | Description |
| --- | --- | --- |
| [AGENTS.md](./AGENTS.md) | Agent Guide | Standards, Playwright E2E testing framework, and repository contribution conventions |
| [README.md](./README.md) | Overview | Getting started with C3 (`create-cloudflare`), dashboard deployment, and testing instructions |


---

## 1. AI Agents & Intelligent Applications

| Template | Description |
| --- | --- |
| [agent-commerce-analytics](./doc/agent-commerce-analytics.md) | Autonomous analytics agent for e-commerce metrics and reporting |
| [agent-visibility](./doc/agent-visibility.md) | Multi-surface content store projecting into `/llms.txt`, JSON-LD, and agent discovery endpoints |
| [ai-brand-visibility](./doc/ai-brand-visibility.md) | Brand visibility auditing and SEO optimization for AI search engines |
| [commerce-llms-txt](./doc/commerce-llms-txt.md) | Exposing product and store catalogs formatted for LLM consumption (`/llms.txt`) |
| [llm-chat-app](./doc/llm-chat-app.md) | Full-stack chat application powered by Workers AI models |
| [text-to-image](./doc/text-to-image.md) | Image generation using Stable Diffusion on Workers AI serverless GPUs |
| [voice-agent](./doc/voice-agent.md) | Real-time full-duplex conversational voice agent using WebSockets |
| [x402-proxy](./doc/x402-proxy.md) | HTTP 402 payment-required proxy for monetizing agent tools and API endpoints |

---

## 2. Databases & Storage (D1, KV, Hyperdrive, R2)

| Template | Description |
| --- | --- |
| [d1](./doc/d1.md) | Serverless SQL database starter using Cloudflare D1 |
| [d1-starter-sessions-api](./doc/d1-starter-sessions-api.md) | Secure user authentication and session management backed by D1 |
| [mysql-hyperdrive](./doc/mysql-hyperdrive.md) | Connecting to existing MySQL databases with connection pooling and caching via Hyperdrive |
| [postgres-hyperdrive](./doc/postgres-hyperdrive.md) | Connecting to PostgreSQL databases globally with low latency via Hyperdrive |
| [r2-explorer](./doc/r2-explorer.md) | File browser and asset manager for Cloudflare R2 object storage |
| [to-do-list-kv](./doc/to-do-list-kv.md) | Key-Value backed stateful task management app using Workers KV |

---

## 3. Full-Stack Web Frameworks

| Template | Description |
| --- | --- |
| [astro-blog-starter](./doc/astro-blog-starter.md) | Fast static and SSR content-driven blog using Astro |
| [next-starter](./doc/next-starter.md) | Full-stack Next.js application deployed to Cloudflare Workers with OpenNext |
| [react-starter](./doc/react-starter.md) | Lightweight React SPA with Workers Static Assets |
| [react-postgres-fullstack](./doc/react-postgres-fullstack.md) | React frontend connected to a PostgreSQL database via Hyperdrive |
| [react-router-starter](./doc/react-router-starter.md) | React Router v7 application running on Workers |
| [react-router-hono-fullstack](./doc/react-router-hono-fullstack.md) | React Router v7 frontend with Hono backend API |
| [react-router-postgres-ssr](./doc/react-router-postgres-ssr.md) | Server-side rendered React Router app with Postgres database |
| [remix-starter](./doc/remix-starter.md) | Modern Remix web framework on Workers |
| [saas-admin](./doc/saas-admin.md) | SaaS admin dashboard with authentication, charts, and table views |
| [vite-react](./doc/vite-react.md) | Vite-powered React client utilizing `@cloudflare/vite-plugin` |

---

## 4. APIs, Containers & Infrastructure

| Template | Description |
| --- | --- |
| [chanfana-openapi](./doc/chanfana-openapi.md) | Auto-generated OpenAPI (Swagger) documentation using Chanfana and Hono |
| [cli](./doc/cli.md) | Command-line interface utilities running on Cloudflare Workers |
| [containers](./doc/containers.md) | Running containerized services on Cloudflare Workers using Docker images |
| [nodejs-http-server](./doc/nodejs-http-server.md) | Node.js HTTP server running on Workers via `nodejs_compat` |
| [openauth](./doc/openauth.md) | Self-hosted universal OAuth authorization server |
| [worker-publisher](./doc/worker-publisher.md) | Publishing content and web assets programmatically to Workers |

---

## 5. Coordination, Durable Objects & Workflows

| Template | Description |
| --- | --- |
| [durable-chat](./doc/durable-chat.md) | Real-time multi-room WebSocket chat backed by Durable Objects |
| [hello-world-do](./doc/hello-world-do.md) | Minimal starter demonstrating stateful Durable Objects |
| [internal-sites](./doc/internal-sites.md) | Hosting internal corporate sites secured by Cloudflare Access |
| [microfrontend](./doc/microfrontend.md) | Composable micro-frontend architecture running on the edge |
| [multiplayer-globe](./doc/multiplayer-globe.md) | Real-time 3D collaborative globe visualization with WebSockets |
| [nlweb](./doc/nlweb.md) | Natural language interface querying web content |
| [workers-builds-notifications](./doc/workers-builds-notifications.md) | Automated build status and deployment notifications |
| [workers-for-platforms](./doc/workers-for-platforms.md) | Multi-tenant platform enabling your users to deploy custom code |
| [workflows-starter](./doc/workflows-starter.md) | Cloudflare Workflows orchestration for durable multi-step processes |
