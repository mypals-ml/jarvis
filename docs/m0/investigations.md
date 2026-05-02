# Milestone 0 Investigation Findings

## 1. Agentic Harness & Orchestration Frameworks
- **Research Findings:**
    - **Claude Code Architecture:** Analysis shows that 98.4% of an agentic system is "deterministic infrastructure" (permissions, context management, tool routing) while only 1.6% is the AI loop.
    - **Orchestration:** **Vercel AI SDK** is highly recommended for streaming-first, multi-provider support (Ollama, Anthropic, OpenAI). It is lightweight compared to LangChain and optimized for modern web/CLI apps.
    - **Harness Pattern:** Decoupling the "Brain" (LLM) from the "Hands" (Harness/Sandbox) is key. The harness should manage the loop, handle tool execution, and enforce safety/permissions.
- **Recommendation:** Use **TypeScript with Vercel AI SDK**. It provides the best balance of speed, streaming support, and robust tool-calling abstractions.

## 2. Language & Distribution Strategy
- **Options Evaluated:**
    - **TypeScript (Node.js/Bun):** Pros: Native for Vercel AI SDK, excellent for terminal-in-browser (xterm.js), large ecosystem for CLI tools (oclif, commander). Cons: Requires Node/Bun runtime.
    - **Python:** Pros: AI standard, good for RAG. Cons: Vercel AI SDK support is secondary, browser terminal integration is less "native" than Node.
    - **Go/Rust:** Pros: Single binary distribution. Cons: AI orchestration libraries are less mature.
- **Recommendation:** **TypeScript (Node.js)**. To solve the "installable on any computer" requirement, we can use tools like `pkg` or `bun build --compile` to create standalone binaries, or distribute via `npm install -g`.

## 3. Remote Terminal over HTTP & Security
- **Technologies:**
    - **Frontend:** **xterm.js** is the industry standard for web-based terminals.
    - **Backend:** `node-pty` (for Node.js) allows spawning real pseudo-terminals on the host.
    - **Communication:** **Socket.io** provides reliable real-time bidirectional communication between the browser and the PTY.
    - **Security:** **Tailscale Funnel** or **Cloudflare Tunnels** are excellent for secure remote access without opening ports. For the browser interface, adding a simple OIDC (OpenID Connect) or basic auth layer is essential.
- **Architecture:** The JARVIS server will host both the AI Agent and a WebSocket server for the terminal. The CLI client will be a thin wrapper that connects to this server or runs locally.

## 4. Proposed Technical Stack for Milestone 0
- **Runtime:** Node.js
- **Orchestration:** Vercel AI SDK
- **LLM Interface:** Ollama (local)
- **Terminal Backend:** `node-pty` + `Socket.io`
- **Terminal Frontend:** `xterm.js`
- **CLI Framework:** `commander` or `oclif`
