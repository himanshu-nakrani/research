# Agent Evaluation & Reliability — Research Landscape (2025-2026)

## Key Benchmarks

| Benchmark | Focus | Best Result | Key Finding |
|---|---|---|---|
| **SWE-bench Verified** | Coding agents | ~29.5% (14B models) | Standard for software agents |
| **GAIA** | General AI assistants | 72.8% (Youtu-Agent) | Multi-step reasoning + tools |
| **AIME 2025** | Math reasoning | 90.0% (ASTER-4B) | RL-trained models dominate |
| **MobileWorld** | Mobile app agents | 51.7% | vs >90% on saturated AndroidWorld |
| **WideSearch** | Agentic info-seeking | 5% success | Even best agents struggle |
| **InnovatorBench** | LLM research agents | Frontier models struggle | Long-horizon tasks |
| **TPS-Bench** | Tool planning & scheduling | — | Novel evaluation angle |
| **MCPAgentBench** | Tool use via MCP | — | Protocol-specific evaluation |
| **PRL-Bench** | Physics research | <50/100 | Real-world research tasks |
| **Robotouille** | Async planning | 47% sync, 11% async | Async is much harder |
| **MindGames Arena** | Social reasoning | 944 agents, 76 teams | NeurIPS 2025 competition |

## Reliability & Failure Analysis

### "Why Do Multi-Agent LLM Systems Fail?" (arXiv:2503.13657, Mar 2025)
- **MAST-Data**: 1,600+ annotated traces from 7 popular MAS frameworks
- **MAST taxonomy**: 14 failure modes in 3 categories:
  1. System Design Issues
  2. Inter-Agent Misalignment
  3. Task Verification
- Key finding: MAS performance gains on benchmarks are often minimal despite hype

### "Interactive Debugging and Steering of Multi-Agent AI Systems" (CHI 2025)
- **AGDebugger**: UI for browsing messages, editing/resetting prior messages
- User study with 14 participants
- Key insight: interactive message resets are crucial for debugging

### "Real AI Agents with Fake Memories" (arXiv:2503.16248, Mar 2025)
- **Memory injection** more dangerous than prompt injection
- Demonstrated unauthorized asset transfers in Web3 agent (ElizaOS)
- **CrAIBench**: 150+ blockchain tasks, 500+ attack test cases
- Fine-tuning defenses more effective than prompt injection detectors

### "AI Agents That Matter" (arXiv:2407.01502, Jul 2024)
- Foundational critique: narrow focus on accuracy ignoring cost
- Advocates joint optimization of accuracy and cost
- Principled framework to avoid benchmark overfitting

## Security & Safety

### MCP Security (arXiv:2503.23278, Mar 2025)
- Model Context Protocol lifecycle: 4 phases → 16 activities
- Threat taxonomy: 4 attacker types → 16 threat scenarios
- Fine-grained security safeguards per lifecycle phase

### DREAM (Compliance-Only Backdoors)
- Models poisoned with compliance-only backdoors
- Attack chains succeed >70% of the time
- PrivacyBench: RAG assistants leak secrets in 26.56% of interactions

## Open Challenges
1. **Temporal reliability degradation** — no paper measures how agent reliability degrades over extended deployment
2. **Failure propagation in multi-agent systems** — one agent's error cascading to others
3. **Graceful failure evaluation** — benchmarks measure success rates but not *how gracefully agents fail*
4. **Cost-normalized evaluation** — no benchmark normalizes performance by compute cost
5. **Cross-environment generalization** — same agent across fundamentally different environments
6. **Adversarial environment testing** — agents under misleading UI elements, deceptive API responses

## Identified Research Gaps
- **Cost-normalized agent evaluation** — benchmarking performance per dollar
- **Agent recovery behavior evaluation** — recovery speed, error communication, fallback strategies
- **Temporal reliability** — measuring degradation over weeks/months of deployment
- **Cross-environment transfer** — evaluating the same agent across web, code, and tool-use environments
