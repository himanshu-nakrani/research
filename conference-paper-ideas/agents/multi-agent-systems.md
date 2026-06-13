# Multi-Agent Systems — Research Landscape (2025-2026)

## Key Developments

### Multi-Agent Training
| Paper | Venue | Contribution |
|---|---|---|
| **Chain-of-Agents (CoA)** | 2025 | Distills multi-agent workflows into a single model via multi-agent distillation and agentic RL |
| **Sotopia-RL** | 2025 | Utterance-level, multi-dimensional rewards for social intelligence |
| **AdvEvo-MARL / Evo-MARL** | 2025 | Co-evolves attackers and defenders to internalize safety |
| **WaltzRL** | 2025 | Jointly trains conversation and feedback agents for safety/helpfulness |
| **DR. WELL** | Nov 2025 | Decentralized neurosymbolic framework with two-phase negotiation |
| **MMedAgent-RL** | 2025 | Multi-agent collaboration for medical reasoning. +23.6% avg gain |
| **Multi²** | ICML 2026 | Hierarchical multi-agent System 1/2 framework |
| **AgentJet** | 2026 | Distributed swarm training for heterogeneous multi-model RL |

### Multi-Agent RAG
- **NightFeats** (NeurIPS 2025 winner): Structured multi-agent RAG with temporal-semantic reranking
- **ReCollab**: Uses RAG to stabilize LLM-based inference for ad-hoc teamwork

### Multi-Agent Planning
- **SPIRAL** (Dec 2025): Symbolic LLM Planning via Grounded and Reflective Search. Three LLM agents (Planner, Simulator, Critic) in MCTS loop. 83.6% on DailyLifeAPIs (+16pp).
- **LoongFlow** (Dec 2025): Directed evolutionary search via cognitive plan-execute-summarize. +60% evolutionary efficiency.

### Communication & Coordination
- **HIS Algorithm**: Shapley-value credit assignment from historical interaction data
- **RALLY**: LLM-driven semantic communication for UAV swarm navigation
- **ProtocolBench** (ICML 2026): Benchmarks multi-agent communication protocols

## Key Findings
1. **Multi-agent gains are often minimal** — MAST-Data shows hype exceeds results on benchmarks
2. **Credit assignment is critical** — Shapley-value methods (HIS) outperform naive approaches
3. **Self-play enables co-evolution** — AdvEvo-MARL shows attacker-defender co-training improves both
4. **Distillation works** — Chain-of-Agents shows multi-agent workflows can be compressed into single models
5. **Communication protocols matter** — ProtocolBench shows protocol choice significantly impacts performance

## Open Challenges
1. **Failure propagation** — How one agent's error cascades to others
2. **Communication efficiency** — Minimizing inter-agent communication while maintaining performance
3. **Scalability** — Training costs scale super-linearly with number of agents
4. **Heterogeneous agents** — Coordinating agents with different capabilities/models
5. **Safety in multi-agent settings** — Emergent unsafe behaviors not present in single agents

## Identified Research Gaps
- **RL for learning communication protocols** — ProtocolBench benchmarks protocols but doesn't learn them end-to-end via RL
- **Failure propagation detection and mitigation** — No systematic framework
- **Cross-environment multi-agent transfer** — Agents trained in one domain transferring to another
- **Memory sharing across agents** — Unexplored for multi-agent systems
