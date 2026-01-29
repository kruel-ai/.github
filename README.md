# kruel.ai

**The first Agent Memory System.**

We build distributed AI with shared memory, reasoning, and identity—agents that persist context, use tools, and improve over time across the stack.

---

## High-level view

kruel.ai is a **Proto-AGI ecosystem**: multiple AI systems that share a common cognitive architecture (memory, tools, persona) and can run side by side for production, experimentation, and evolution.

| System | Role | Architecture |
|--------|------|--------------|
| **kruel-v8-manns** | Production Proto-AGI | HTTP API, 42 tools, MCP, dual memory, TTS. Primary production server. |
| **K9-spark** | KRUEL-V9 AGI | WebSocket + subsystems, dedicated Neo4j, React frontend. Predecessor to V8, still in use. |
| **KX** | Experimental refactor | FastAPI, single-agent loop (CompleteAgent pipeline). Simplified orchestration, same memory stack. |

All three use the same **memory backbone** (Neo4j + FAISS), **MCP (Model Context Protocol)** for tools and context, and **LLM integration** (Ollama, llama.cpp, OpenAI-compatible, Nemotron). They differ in orchestration style and deployment.

---

## Shared architecture

- **Dual memory** — Neo4j for graph/entities/temporal queries; FAISS for semantic vector search. One backbone, shared across instances.
- **MCP** — Memory tools (`store` / `retrieve` / `context`), code tools (`search` / `kruel_code`), communication (`kruel_communicate`), and cognitive tools (`evaluate_reasoning`, `check_beliefs`).
- **LLM** — Local (llama.cpp, Ollama) and API (OpenAI-compatible, Nemotron). Same persona and memory context regardless of backend.
- **Workflow** — User input → intent → orchestration → tool selection & execution → memory update → response (and optional TTS). KX compresses this into a single CompleteAgent pipeline (Now Memory → Context → Persona → Goal → Tools → Guidance → LLM → Store).

Frontends (e.g. K9 React app, KXclient desktop overlay) and infra (Docker, spark-build) sit on top of these backends.

---

## Repositories

This org holds the **kruel.ai** codebase and related projects: production and experimental AI servers, frontends, inference stacks, and infrastructure. We're organizing repos and defaults here (`.github`) so the whole org stays consistent and easy to navigate.

- **Production AI**: kruel-v8-manns, K9-spark  
- **Experimental**: KX (kx-server)  
- **Clients & frontends**: k9-frontend, KXclient  
- **Infrastructure**: spark-build (Docker/compose), playbooks  
- **Inference & models**: llama.cpp, Nemotron, ComfyUI, intent_service, etc.

---

[kruel.ai](https://kruel.ai) · [bparry@kruel.ai](mailto:bparry@kruel.ai) · [LinkedIn](https://www.linkedin.com/in/bennett-parry-96441184)
