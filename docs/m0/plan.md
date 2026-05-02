# JARVIS Project Plan

This document outlines the phased implementation of JARVIS, a private, local home-hosted AI assistant.

## Milestone 0: CLI Code Assistant & System Foundation
**Goal:** Establish the core agentic architecture and provide a powerful CLI for local development and system management.

*   **Investigation: Agentic Harness & Orchestration Frameworks.** Research the "Harness" architectural pattern where the agent is decoupled from the LLM server (inspired by Claude Code and similar research). Compare Vercel AI SDK, LangChain, and custom implementations.
*   **Investigation: Language & Distribution Strategy.** Evaluate TypeScript/Node.js, Python, and Go/Rust. Focus on ease of installation as a CLI on remote machines vs. building a robust web-server for the terminal interface.
*   **Investigation: Remote Terminal over HTTP & Security.** Research technologies for a "terminal-like experience in the browser" (e.g., xterm.js, Socket.io) and secure proxy/tunnelling options (Tailscale, Cloudflare, etc.).
*   **Implementation: Core Agent Server.** Set up the central server that interfaces with Ollama and manages agent state.
*   **Implementation: CLI Client.** Create the installable CLI tool that connects to the JARVIS server.
*   **Implementation: Tooling.** Implement basic shell and filesystem tools with support for both autonomous and human-in-the-loop modes.
*   **Implementation: Web Terminal UI.** Deploy the terminal-based browser interface.

## Milestone 1: Knowledge & Long-Term Memory
**Goal:** Enhance the assistant with the ability to retrieve real-time information and remember user context.

*   **Investigation: Local RAG Stack.** Evaluate local-first vector databases (ChromaDB, LanceDB, etc.) and their integration via MCP.
*   **Implementation: Web Search.** Add tools for real-time internet information retrieval.
*   **Implementation: Memory System.** Enable the assistant to store and retrieve context from previous interactions and local project files.

## Milestone 2: Voice Interaction & Ambient Presence
**Goal:** Enable eyes-free interaction through high-quality local voice processing.

*   **Implementation: Speech-to-Text (STT).** Integrate OpenAI Whisper (local) for processing voice commands.
*   **Implementation: Text-to-Speech (TTS).** Integrate Piper for low-latency, high-quality local voice responses.
*   **Implementation: Voice Protocol.** Implement Wyoming protocol support to allow JARVIS to interact with satellite microphones/speakers.

## Milestone 3: Smart Home Mastery
**Goal:** Fully integrate with the home environment for device control and sensor monitoring.

*   **Implementation: Home Assistant Integration.** Connect JARVIS to the Home Assistant API.
*   **Implementation: Home Tools.** Create tools for the agent to query sensor data and control local IoT devices (lights, climate, etc.).
*   **Refinement:** Finalize the "Domestic AI" experience with unified control across CLI, Web, and Voice.
