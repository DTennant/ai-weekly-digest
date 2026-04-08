# Digest #5 — Agent Memory & Persistence: Reading List

*Compiled 2025-06-30 for AI Weekly Digest*

---

## 🌐 Landscape Overview

Agent memory has exploded from a niche research concern into the central engineering challenge of 2025 agentic AI. The field is converging on a layered view inspired by human cognition: **sensory/working memory** (context window), **episodic memory** (past experiences), **semantic memory** (facts & knowledge graphs), and **procedural memory** (learned behaviors). Several competing paradigms are crystallizing — Mem0's extract-and-consolidate approach, Letta/MemGPT's OS-style tiered memory management, Zep/Graphiti's temporal knowledge graphs, and LangChain's new LangMem SDK with its semantic/episodic/procedural taxonomy. Meanwhile, two new "operating system" framings have emerged: **MemOS** (treating memory as a first-class schedulable resource) and **Memory as a Service (MaaS)** (memory as cross-agent service modules). On the product side, OpenAI shipped comprehensive cross-conversation memory in ChatGPT (April 2025), Anthropic is preparing a memory feature for Claude, and Letta launched both the Agent File (.af) portable state format and the Letta Leaderboard benchmark. The research community is catching up with new benchmarks (MemBench, MemAE, Letta Leaderboard) and growing concern about privacy/security risks of persistent memory.

---

## 📚 Research Papers (sorted by relevance)

### Tier 1: Essential Reading (Relevance 5/5)

---

**1. Mem0: Building Production-Ready AI Agents with Scalable Long-Term Memory**
- **Authors:** Mem0.ai team (Deshpande et al.)
- **Date:** April 28, 2025
- **Link:** https://arxiv.org/abs/2504.19413
- **Summary:** Introduces a scalable memory-centric architecture that dynamically extracts, consolidates, and retrieves salient information from ongoing conversations. Addresses the fundamental "reset" problem — LLMs lose all context outside their window — with a production-ready system for persistent conversational coherence. Benchmarks show 26% improvement over baseline on long-term memory tasks.
- **Relevance:** ⭐⭐⭐⭐⭐ — The most directly production-relevant paper. Bridges research and deployment.
- **Angles:** Long-term memory architectures, memory consolidation, persistent identity

---

**2. MemOS: An Operating System for Memory-Augmented Generation in LLMs**
- **Authors:** China Telecom research team
- **Date:** May 28, 2025
- **Link:** https://arxiv.org/abs/2505.22101
- **Summary:** Proposes elevating memory to a "first-class operational resource" in LLMs, analogous to how operating systems manage hardware resources. Introduces lifecycle management, multi-modal memory integration, and schedulable memory operations. Addresses "memory silos" across platforms and the inability to reuse prior interactions.
- **Relevance:** ⭐⭐⭐⭐⭐ — Bold architectural vision. The OS metaphor for memory is a powerful framing for the digest.
- **Angles:** Long-term memory architectures, memory consolidation, file-system vs. vector DB vs. hybrid

---

**3. A-MEM: Agentic Memory for LLM Agents**
- **Authors:** Xu et al.
- **Date:** Feb 2025 (updated May 30, 2025)
- **Link:** https://arxiv.org/abs/2502.12110
- **Summary:** Introduces a self-organizing memory system inspired by the Zettelkasten method. Instead of predefined memory operations, agents dynamically create interconnected "atomic notes" with rich contextual descriptions, forming an evolving knowledge network. Enables multi-hop reasoning through emergent memory connections.
- **Relevance:** ⭐⭐⭐⭐⭐ — Elegant design that lets agents be their own memory architects. Great "lived experience" angle.
- **Angles:** Long-term memory architectures (RAG, episodic, semantic), "lived experience," memory consolidation

---

**4. Rethinking Memory in AI: Taxonomy, Operations, Topics, and Future Directions**
- **Authors:** Du, Huang, Zheng, Wang et al.
- **Date:** May 1, 2025 (updated May 27, 2025)
- **Link:** https://arxiv.org/abs/2505.00675
- **Summary:** Comprehensive taxonomy paper that maps the entire memory landscape. Covers parametric vs. non-parametric memory, memory operations (read/write/update/forget), and surveys frameworks like Graphiti, LlamaIndex, LangChain, LangGraph, CrewAI, and Letta. Provides a unified vocabulary for the field.
- **Relevance:** ⭐⭐⭐⭐⭐ — Essential reference for understanding the taxonomy. Good "lay of the land" paper.
- **Angles:** All angles — comprehensive survey

---

**5. From Human Memory to AI Memory: A Survey on Memory Mechanisms in the Era of LLMs**
- **Authors:** Wu et al.
- **Date:** April 22, 2025
- **Link:** https://arxiv.org/abs/2504.15965
- **Summary:** Maps human memory systems (episodic, semantic, procedural) to their AI analogs. Distinguishes non-parametric long-term memory (user-specific storage/retrieval ≈ episodic) from parametric long-term memory (knowledge embedded in weights ≈ semantic). Provides a cognitive science lens on the engineering challenge.
- **Relevance:** ⭐⭐⭐⭐⭐ — Best paper for the "human cognition → AI architecture" narrative thread.
- **Angles:** Long-term memory architectures, memory consolidation, episodic vs. semantic

---

### Tier 2: Highly Relevant (Relevance 4/5)

---

**6. How Memory Management Impacts LLM Agents: An Empirical Study of Experience-Following Behavior**
- **Authors:** Xiong et al.
- **Date:** May 21, 2025
- **Link:** https://arxiv.org/abs/2505.16067
- **Summary:** Empirical study revealing the "experience-following property" — agents closely mimic past executions when similar inputs appear. Identifies two critical failure modes: error propagation (bad memories compound) and misaligned experience replay (correct-looking but misleading memories). Shows that future task evaluations can serve as quality labels for stored memory.
- **Relevance:** ⭐⭐⭐⭐ — Important cautionary results. Memory isn't just about storage — quality control matters.
- **Angles:** "Lived experience" as knowledge, memory consolidation (forgetting)

---

**7. MemEngine: A Unified and Modular Library for Developing Advanced Memory of LLM-based Agents**
- **Authors:** Zhang et al.
- **Date:** May 4, 2025
- **Link:** https://arxiv.org/abs/2505.02099
- **Summary:** Open-source library that implements multiple memory models (FullMemory, RetrievalMemory, RecentMemory, etc.) in a unified framework. Enables plug-and-play comparison of memory mechanisms. Used as the foundation for the MemBench benchmark.
- **Relevance:** ⭐⭐⭐⭐ — Practical engineering contribution. Good for the "tools you can use today" angle.
- **Angles:** Long-term memory architectures, file-system vs. vector DB vs. hybrid

---

**8. Collaborative Memory: Multi-User Memory Sharing in LLM Agents with Dynamic Access Control**
- **Authors:** Rezazadeh, Zhao et al.
- **Date:** May 23, 2025
- **Link:** https://arxiv.org/abs/2505.18279
- **Summary:** First systematic framework for multi-user, multi-agent memory management with asymmetric and dynamic access constraints. Addresses: who can share what memory, when, and with whom? Tackles the key challenge of maximizing collective memory utility while enforcing permission boundaries.
- **Relevance:** ⭐⭐⭐⭐ — Uniquely addresses memory in multi-agent systems with real access control concerns.
- **Angles:** Memory in multi-agent systems (shared memory, protocols)

---

**9. Memory as a Service (MaaS): Rethinking Contextual Memory as Service-Oriented Modules for Collaborative Agents**
- **Authors:** Li et al.
- **Date:** June 28, 2025
- **Link:** https://arxiv.org/abs/2506.22815
- **Summary:** Proposes treating memory as a service that can be consumed across agent boundaries. Introduces a two-dimensional design space (entity structure × service type) and maps how MaaS extends current memory practices to cross-entity collaboration. Outlines governance, security, and ethical considerations.
- **Relevance:** ⭐⭐⭐⭐ — Forward-looking architectural vision for memory interop across agent systems.
- **Angles:** Memory in multi-agent systems, file-system vs. vector DB vs. hybrid approaches

---

**10. Procedural Memory Is Not All You Need: Bridging Cognitive Gaps in LLM-Based Agents**
- **Authors:** Wheeler & Jeunen
- **Date:** May 6, 2025 (ACM UMAP '25 workshop)
- **Link:** https://arxiv.org/abs/2505.03434
- **Summary:** Argues that LLMs are fundamentally constrained by reliance on procedural memory alone. In "wicked" environments (shifting rules, ambiguous feedback, novelty), agents need semantic memory and associative learning. Proposes modular architectures that decouple cognitive functions.
- **Relevance:** ⭐⭐⭐⭐ — Great conceptual piece on why memory diversity matters. Pairs well with the surveys.
- **Angles:** Long-term memory architectures, memory consolidation

---

**11. Ella: Embodied Social Agents with Lifelong Memory**
- **Authors:** Zhang et al. (UMass)
- **Date:** June 30, 2025
- **Link:** https://arxiv.org/abs/2506.24019
- **Summary:** Introduces embodied social agents in a 3D open world with lifelong multimodal memory: name-centric semantic memory for knowledge and spatiotemporal episodic memory for experiences. 15 agents engage in social activities for days, demonstrating learning through observation and social interaction. Shows agents can influence, lead, and cooperate with others.
- **Relevance:** ⭐⭐⭐⭐ — Compelling demo of "lived experience" in embodied multi-agent setting.
- **Angles:** "Lived experience" as knowledge, memory in multi-agent systems, episodic + semantic memory

---

**12. MemBench: Towards More Comprehensive Evaluation on the Memory of LLM-based Agents**
- **Authors:** Tan et al.
- **Date:** June 20, 2025
- **Link:** https://arxiv.org/abs/2506.21605
- **Summary:** Presents a comprehensive benchmark evaluating agent memory across effectiveness, efficiency, and capacity dimensions. Built on MemEngine, implements seven memory mechanisms with Qwen2.5-7B as base model. Provides systematic evaluation beyond simple recall accuracy.
- **Relevance:** ⭐⭐⭐⭐ — Key benchmark paper. Essential for the "how do we measure this?" question.
- **Angles:** Benchmarks for agent memory

---

**13. AgentRR: Get Experience from Practice — LLM Agents with Record & Replay**
- **Authors:** Feng et al.
- **Date:** May 23, 2025
- **Link:** https://arxiv.org/abs/2505.17716
- **Summary:** Introduces record-and-replay for AI agents: record interaction traces during task execution, summarize into structured "experiences," replay in similar future tasks. Features multi-level experience abstraction and check functions as trust anchors. Envisions an experience repository for cross-agent knowledge sharing.
- **Relevance:** ⭐⭐⭐⭐ — Novel paradigm for "lived experience" memory. Bridges reliability and learning.
- **Angles:** "Lived experience" as knowledge, memory consolidation, persistent identity

---

### Tier 3: Worth Noting (Relevance 3/5)

---

**14. Cognitive Memory in Large Language Models**
- **Authors:** Shan et al.
- **Date:** April 3, 2025
- **Link:** https://arxiv.org/abs/2504.02441
- **Summary:** Comprehensive technical analysis of memory mechanisms at the systems level: text-based memory, KV cache management, parameter-based memory (LoRA/TTT/MoE), and hidden-state approaches. Covers the full stack from acquisition through compression to utilization.
- **Relevance:** ⭐⭐⭐ — More technical/systems-level. Good reference for implementers.
- **Angles:** Long-term memory architectures, file-system vs. vector DB vs. hybrid

---

**15. Unveiling Privacy Risks in LLM Agent Memory**
- **Authors:** Wang et al.
- **Date:** Feb 2025 (updated June 3, 2025)
- **Link:** https://arxiv.org/abs/2502.13172
- **Summary:** Proposes MEXTRA (Memory Extraction Attack) — a black-box attack that extracts private information from agent memory systems. Demonstrates that persistent memory creates new attack surfaces. Explores factors influencing memory leakage from both designer and attacker perspectives.
- **Relevance:** ⭐⭐⭐ — Important counterpoint. Memory persistence has a dark side.
- **Angles:** Persistent identity / security implications

---

**16. AriGraph: Learning Knowledge Graph World Models with Episodic Memory for LLM Agents**
- **Authors:** Anokhin et al.
- **Date:** July 2024 (updated May 15, 2025)
- **Link:** https://arxiv.org/abs/2407.04363
- **Summary:** Represents agent memory as a structured knowledge graph encoding both semantic facts and episodic events. Enables grounded world modeling for agent decision-making through graph-structured recall.
- **Relevance:** ⭐⭐⭐ — Good example of the knowledge-graph approach to memory.
- **Angles:** Long-term memory architectures (episodic + semantic), "lived experience"

---

**17. MemAE: Evaluating Memory in LLM Agents via Incremental Multi-Turn Interactions**
- **Authors:** (OpenReview submission)
- **Date:** June 10, 2025
- **Link:** https://openreview.net/forum?id=ZgQ0t3zYTQ
- **Summary:** Unified evaluation framework for memory agents covering four identified memory competencies. Combines reformulated existing datasets with newly constructed ones for systematic assessment.
- **Relevance:** ⭐⭐⭐ — Another benchmark entry, complementary to MemBench.
- **Angles:** Benchmarks for agent memory

---

**18. SAGE: Self-evolving Agents with Reflective and Memory-augmented Abilities**
- **Authors:** He et al.
- **Date:** Sept 2024 (updated April 20, 2025)
- **Link:** https://arxiv.org/abs/2409.00872
- **Summary:** Agents that self-evolve through reflection and memory augmentation, adapting to ambiguous prompts through human-machine co-adaptation.
- **Relevance:** ⭐⭐⭐ — Interesting self-improvement angle.
- **Angles:** Memory consolidation, "lived experience"

---

## 🏢 Industry Developments & Product Announcements

### Major Platform Moves

**OpenAI — Comprehensive ChatGPT Memory (April 10, 2025)**
- ChatGPT now references ALL past conversations, not just explicit "memories"
- Creates continuous personalization based on interaction history
- Significant privacy debate (Simon Willison's "memory dossier" critique)
- Link: https://techcrunch.com/2025/04/10/openai-updates-chatgpt-to-reference-your-other-chats/

**Anthropic — Claude Memory Feature (In Development, June 2025)**
- Memory feature discovered in development (June 24, 2025) that will allow Claude to reference previous conversations
- Claude 4 (May 22, 2025) already features improved long-term memory when given file access — creates and updates "memory files" to track progress
- Link: https://www.testingcatalog.com/anthropic-developing-memory-and-ai-powered-artifacts-for-claude/

### Framework & SDK Releases

**LangChain — LangMem SDK (May 13, 2025)**
- New SDK for agent long-term memory with three memory types: semantic (facts/knowledge), episodic (past experiences), procedural (behavioral patterns)
- Storage patterns: "Profiles" (current state) vs. "Collections" (searchable knowledge base)
- Integrates natively with LangGraph's persistent memory layer
- Managed service available for production use
- Link: https://blog.langchain.com/langmem-sdk-launch/

**LlamaIndex — Flexible Memory API (May 2025)**
- New Memory API with plug-and-play blocks: StaticMemoryBlock, FactExtractionMemoryBlock, VectorMemoryBlock
- Combines short-term chat history with long-term memory in modular architecture
- Link: https://www.llamaindex.ai/blog/llamaindex-newsletter-2025-05-20

**Letta — Agent File (.af) Format (April 2, 2025)**
- Open file format for serializing stateful agents with persistent memory and behavior
- Human-readable representation of all agent state — portable across machines/runtimes
- Enables version control, debugging, and sharing of complete agent states
- Link: https://www.letta.com/blog/agent-file

**Letta — Letta Leaderboard (May 29, 2025)**
- Comprehensive benchmark for agentic memory management: reading, writing, updating
- Evaluates core memory (in-context) and archival memory (external) operations
- Fills gap — existing LLM leaderboards ignore memory capabilities
- Link: https://www.letta.com/blog/letta-leaderboard

**Letta — Memory Blocks Architecture (May 14, 2025)**
- Detailed design for structured memory tiers with agent-managed context
- Core memory (in-context window) + archival memory (external store)
- Link: https://www.letta.com/blog/memory-blocks

### Emerging Tools

**Zep / Graphiti — Temporal Knowledge Graphs for Agent Memory**
- Knowledge graph engine with temporal awareness — tracks how entities/relationships change over time
- 18% accuracy improvement on LongMemEval benchmarks
- MCP Memory Service available for cross-platform use
- Positioning: "Stop Using RAG for Agent Memory"
- Link: https://blog.getzep.com/stop-using-rag-for-agent-memory/

**Hindsight — Agent Memory That Learns (June 2025)**
- Open-source memory system with retain/recall API and MCP server integration
- Temporal awareness with timestamps for memory evolution tracking
- Link: https://github.com/vectorize-io/hindsight

**SuperMemory MCP — Universal Memory Across LLMs**
- Standardized MCP server for portable user memory across different AI platforms
- Link: Referenced in MCP ecosystem discussions

**Mem0 — Memory Provider Benchmark (April 29, 2025)**
- Benchmarked OpenAI Memory vs LangMem vs MemGPT vs Mem0
- Mem0 leads with 66.9% accuracy and 1.4s latency
- Link: https://mem0.ai/blog/benchmarked-openai-memory-vs-langmem-vs-memgpt-vs-mem0-for-long-term-memory-here-s-how-they-stacked-up

---

## 🔑 Key Themes for the Digest

1. **Memory as Infrastructure** — The shift from "memory as a feature" to "memory as a first-class system resource" (MemOS, Letta's OS metaphor, MaaS)

2. **The Forgetting Problem** — Error propagation through bad memories, the need for memory quality control, selective forgetting (paper #6 is key here)

3. **Competing Storage Paradigms** — Vector DB (Mem0) vs. Knowledge Graphs (Zep/Graphiti) vs. File-based (Letta, Claude 4's memory files) vs. Hybrid approaches

4. **Benchmarking Gap Closing** — MemBench, MemAE, Letta Leaderboard all launched within weeks of each other — the field now has evaluation infrastructure

5. **Multi-Agent Memory** — Collaborative Memory, MaaS, and Agent2Agent protocol signal that shared memory across agents is the next frontier

6. **Privacy/Security Tension** — OpenAI's "memory dossier" controversy + MEXTRA attack paper highlight that persistent memory creates persistent risks

7. **The Experience Paradigm** — AgentRR, Ella, and A-MEM all point toward agents that learn from doing, not just from training data

---

## 📖 Suggested Blog Posts for Deep Dives

- **"Memory: The Key to Coherent, Long-Lived LLM Agents"** — Samira Ghodratnama (May 2025): Excellent overview comparing Mem0, Graphiti, Letta approaches
  - https://samiranama.com/posts/Memory-and-Context-The-Key-to-Smarter-Autonomous-AI-Agents/

- **"Deep Dive into 'Memory for LLMs' Architectures"** — Machine Learning at Scale (March 2025): Technical comparison of memory architectures
  - https://machinelearningatscale.substack.com/p/deep-dive-into-memory-for-llms-architectures

- **"LLM Agentic Memory Systems"** — Ahmed's Blog (March 2025): Good primer on the cognitive science foundations
  - https://kickitlikeshika.github.io/2025/03/22/agentic-memory.html

- **"Memory in AI: MCP, A2A & Agent Context Protocols"** — Orca Security (May 2025): Security-focused view of memory protocols
  - https://orca.security/resources/blog/bringing-memory-to-ai-mcp-a2a-agent-context-protocols/

- **"Stateful Agents with Letta.ai"** — Machine Learning at Scale (June 2025): Practical guide to Letta's two-tiered memory
  - https://machinelearningatscale.substack.com/p/stateful-agents-with-lettaai
