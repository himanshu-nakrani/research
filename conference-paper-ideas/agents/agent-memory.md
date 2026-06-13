# Agent Memory Architectures — Research Landscape (2025-2026)

## Key Systems

### MemMachine (arXiv:2604.04853, Apr 2026)
- Open-source system with **short-term, long-term episodic, and profile memory**
- Ground-truth-preserving retrieval
- 93.0% on LongMemEvalS, ~80% fewer tokens than Mem0

### Mem-α (arXiv:2509.xxxxx, Sep 2025)
- RL framework for teaching agents memory construction
- Core, episodic, semantic components
- Generalizes from ≤30k training tokens to >400k tokens (13x)

### MEMTIER
- Tripartite memory architecture (episodic JSONL, weighted retrieval, cognitive weight update)
- Addresses **14pp tool success degradation over 72hrs** — key finding for long-running agents

### Evo-Memory (Nov 2025)
- Benchmarks agent test-time learning with self-evolving memory
- 10+ memory modules across 10 datasets

### Field-Theoretic Memory
- Models memory as continuous semantic fields governed by PDEs
- +116% F1 on multi-session reasoning

### "Intelligent Decay" (arXiv:2509.xxxxx, Sep 2025)
- Hybrid episodic-semantic memory with composite scoring (recency, relevance, utility) for pruning

## Key Findings
1. **Memory inflation is real** — MEMTIER shows 14pp performance drop over 72hrs without active management
2. **Hybrid architectures outperform** — combining episodic + semantic + profile memory beats any single type
3. **RL-trained memory construction** (Mem-α) generalizes far beyond training context lengths
4. **Intelligent decay/pruning** is essential — naive memory accumulation degrades performance

## Open Challenges
1. **Memory coherence over long deployments** — no principled solution for maintaining consistency
2. **Memory security** — "Real AI Agents with Fake Memories" (arXiv:2503.16248) showed memory injection is more dangerous than prompt injection
3. **Cross-session memory transfer** — sharing learned knowledge across different agent instances
4. **Memory-efficiency tradeoff** — more memory helps reasoning but increases latency and cost

## Identified Research Gaps
- No paper studies **temporal memory degradation** systematically across different agent architectures
- No framework for **memory-aware RL training** — agents don't learn to manage their own memory via RL
- **Cross-agent memory sharing** for multi-agent systems is unexplored
