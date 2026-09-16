# Cloudflare Sandbox SDK

The Cloudflare Sandbox SDK enables secure, isolated code execution inside Linux containers directly from [Cloudflare Workers](https://developers.cloudflare.com/workers/). Run untrusted user code, execute commands, manage files, manage background processes, and expose dynamic container services.

## Overview

Cloudflare Sandbox bridges edge serverless compute with containerized environments. It provides:
- **Command Execution**: Run synchronous or streaming commands with real-time stdout/stderr capture.
- **File System Operations**: Read, write, upload, and stream files into isolated container storage.
- **Process Management**: Run long-lived background daemons, servers, and processes with health monitoring.
- **Port Exposure & Tunneling**: Expose HTTP services running inside containers directly through your Worker.
- **Jupyter & Python Kernel**: Execute interactive Python sessions, notebooks, and REPL evaluations.

## Quick Start

### 1. Installation

```bash
npm install @cloudflare/sandbox
```

### 2. Configure Dockerfile & Wrangler

Reference the official Cloudflare Sandbox container image in your `Dockerfile`:

```dockerfile
FROM cloudflare/sandbox:0.12.9
```

In `wrangler.toml` (or `wrangler.jsonc`):

```toml
[containers]
image = "./Dockerfile"
max_instances = 5
```

### 3. Usage in a Worker

```typescript
import { getSandbox } from "@cloudflare/sandbox";

export default {
  async fetch(request: Request, env: Env): Promise<Response> {
    const sandbox = getSandbox(env.SANDBOX);

    // Run a command inside the container
    const result = await sandbox.exec("python3", ["-c", "print(1 + 1)"]);
    return new Response(result.stdout);
  }
};
```

## Documentation Index

See [index.md](./index.md) for the complete directory of architecture documents, guides, and skills.
