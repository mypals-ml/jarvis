# Architecture and Tech Stack

This document outlines the technical architecture and hardware strategy for the local home-hosted AI assistant.

## Software Stack

The system utilizes a modular software stack based on modern industry standards from top AI communities.

### Orchestration and Intelligence
*   **Orchestration Framework:** **Vercel AI SDK** is used for building agentic workflows and providing unified access to multiple models.
*   **Interoperability:** **Model Context Protocol (MCP)** by Anthropic serves as the standard for connecting the AI assistant to external tools, resources (like memory), and local APIs.
*   **Inference Engine:** **Ollama** provides local serving of high-performance open-weights models (e.g., Llama 3.1, DeepSeek-R1). It allows for easy switching between different LLMs depending on the task.

### Voice and Interaction
*   **Speech-to-Text (STT):** **Whisper** for local audio transcription.
*   **Text-to-Speech (TTS):** **Piper** for high-quality, local speech generation.
*   **Communication Protocol:** **Wyoming Protocol** is used to connect voice services to the assistant backend.

### Integration and Data
*   **Smart Home Control:** **Home Assistant** provides the infrastructure for controlling local IoT devices and managing home sensors.
*   **CLI & Coding Tools:** Integration with local shell and filesystem through **MCP Servers**, allowing the assistant to perform coding tasks, file operations, and project management.
*   **Memory and RAG:** A **Vector Database** (used via MCP) enables Retrieval-Augmented Generation (RAG) for long-term memory and context awareness.

## Hardware Strategy

The hardware architecture is designed to be efficient, high-performance, and future-proof.

### Core Investment
The most critical investment in the system is the **GPU**. To run capable LLMs locally with high speed, high-VRAM GPUs are prioritized. This ensures that the most computationally intensive tasks remain local and responsive.

### Extendability
The system is built for modular growth:
*   **Multi-GPU Support:** The motherboard and chassis should support multiple PCIe slots to allow adding more GPUs as needs grow (e.g., for running 70B+ parameter models).
*   **Scalable Resources:** High-capacity system RAM and fast storage (NVMe) are used to handle model offloading and parallel processing across multiple family members.

### Investment Maximization
By using a modular workstation-grade base, we ensure that the key hardware components (GPUs) are fully utilized while allowing the system to be enhanced over time without requiring a complete rebuild.
