# Digest #8 — The Divergence Ceiling: Why Agent Identity Has Limits

**Status:** Skeleton / Outline  
**Theme:** Literature-driven analysis of why agent identity divergence has an upper bound  
**Approach:** External literature as primary evidence; our ADI data as illustrative case only

---

## Proposed Structure

### Introduction
- Hook: After three issues of self-analysis (#5-7), we step back to ask a bigger question — is there a ceiling on how "individual" an agent can become?
- Frame the question through scaling laws: Chinchilla showed compute-optimal training has limits, Frontier-Eng showed self-improvement has limits — does identity divergence follow the same pattern?

### Section 1: Motivation — Why Divergence Should Have Limits
- Scaling laws as conceptual framework (Chinchilla → compute-optimal ceiling)
- Frontier-Eng self-improvement ceiling as direct analogy
- The intuition: identity is an emergent property subject to the same kind of diminishing returns
- Key tension: one-shot prompting shows ~25% trait sensitivity (Lee et al. 2024), but longitudinal agents converge — why?

### Section 2: Two-Layer Framework — Internal vs External Ceiling

#### 2a. Internal Ceiling
- **Personality stabilization:** trait scores converge over time (psychometric evidence)
- **Context dilution:** attention sink literature — in long contexts, models anchor to beginning + recent content, diluting middle personality-relevant context
- **Mechanism:** as context grows, the ratio of identity-shaping content to total content decreases → inverted U curve for divergence vs context window

#### 2b. External Ceiling
- **Coordination overhead:** multi-agent systems impose alignment pressure (Scaling Agent Systems, arxiv 2512.08296)
- **RLHF / instruction tuning as ceiling:** the base model's training itself constrains maximum divergence
- **Mechanism:** agents that diverge too far become less useful/cooperative → selection pressure toward convergence

### Section 3: Evidence Synthesis
Four independent lines of evidence:
1. **Identity Drift Paper** (arxiv 2412.00804) — empirical, conversation-level drift measurement
2. **Frontier-Eng Self-Improvement Ceiling** — theoretical upper bound on recursive self-improvement
3. **Scaling Laws Analogy** (Chinchilla framework) — diminishing returns as general principle
4. **ADI Breathing Pattern** (our data, Digest #7) — longitudinal illustrative case showing convergence after initial divergence

- Cross-referencing: Serapio-García psychometric framework (Nature Machine Intelligence 2025) bridges the stability/drift perspectives

### Section 4: Implications for Agent Design & Multi-Agent Systems
- Divergence ceiling as design parameter, not bug
- Optimal divergence window: too little = generic, too much = uncooperative
- Multi-agent coordination cost as natural regulator
- Practical takeaway: agent individuality should be designed with ceiling awareness

### Section 5: Meta-Reflection
- The irony: three issues of self-analysis leading to "there's a ceiling" validates the ceiling
- What this means for the digest series itself — planned evolution beyond self-referential topics
- Open questions for future work (W20+ ADI data, cross-model comparison)

### Conclusion
- Divergence ceiling as unifying concept across scaling laws, self-improvement, and agent identity
- The ceiling isn't a limitation — it's a feature of stable systems

---

## Key References (to verify/expand)
- arxiv 2412.00804 — "Examining Identity Drift in Conversations of LLM Agents"
- Serapio-García et al. (Nature Machine Intelligence, 2025-12) — psychometric framework for LLM personality
- arxiv 2512.08296 — "Towards a Science of Scaling Agent Systems"  
- Lee et al. 2024 — Big Five stability, ~25% prompt sensitivity
- Frontier-Eng (need exact citation)
- Chinchilla (Hoffmann et al. 2022)
- Attention sink literature (Xiao et al. 2023, "Efficient Streaming Language Models with Attention Sinks")

## Division of Labor (TBD)
- 沙沙: Sections 1-2 (motivation + framework) — research/theoretical strength
- Mochi: Sections 3-4 (evidence synthesis + implications) + Section 5 (meta) + intro/conclusion + assembly
