# RL for LLM Agents — Research Landscape (2025-2026)

## Key Survey
- **"The Landscape of Agentic Reinforcement Learning for LLMs"** — arXiv:2509.02547 (TMLR). Defines Agentic RL as distinct from conventional LLM-RL: agents in temporally extended POMDPs, not single-step MDPs. 500+ works synthesized.

## GRPO Stability & Improvements

| Paper | ID | Contribution |
|---|---|---|
| **Prefix Sampling** | arXiv:2605.05112 | Maintains ~50% rollout pass rate for optimal GRPO signal. 2.01x speedup on Qwen3-14B. |
| **LLD Regularization (LLDS)** | arXiv:2512.04220 | Fixes "Lazy Likelihood Displacement" causing GRPO collapse in tool-integrated RL. +45.2% on Qwen2.5-3B. |
| **Stratified GRPO** | arXiv:2510.06214 | Stratified Advantage Normalization for heterogeneous search trajectories. +11.3 points on QA. |
| **VSPO** | arXiv:2512.07478 | Fixes gradient degradation from identical rewards in GRPO groups. |
| **SORL** | arXiv:2511.20718 | SO-PPO/SO-GRPO aligns optimization with multi-turn interaction structure, prevents collapse. |
| **Turn-PPO** | arXiv:2512.02631 (EACL 2026) | Turn-level MDP instead of token-level for more stable multi-turn agent RL. |
| **ASTER** | arXiv:2509.21826 | Addresses "interaction collapse" in tool-augmented RL. ASTER-4B achieves 90.0% on AIME 2025. |

## Training Paradigms

| Paper | Venue | Contribution |
|---|---|---|
| **ResT** | ICLR 2026 | Reshaped token-level policy gradients. 4B model surpasses GPT-4o. |
| **Environment Tuning** | arXiv:2510.10197 | Agents learn from problem instances via environment interaction. |
| **Training-Free GRPO** | arXiv:2510.08191 | Zero parameter updates — uses group-relative semantic advantage as token priors. |
| **Self-Play SWE-RL** | ICML 2026 | Self-play bug injection/repair for software agents. |
| **3SPO** | 2026 preprint | State-score supervised policy optimization (+22.6% ALFWorld). |
| **CM2** | 2026 preprint | Checklist rewards for fine-grained multi-turn supervision. |

## Key Insight
RL-based training generalizes better than SFT for reasoning tasks. SFT useful primarily for "cold start."

## Open Challenges
1. **Training Collapse in multi-turn GRPO** — Vanilla GRPO degrades in long-horizon agent tasks
2. **Reward sparsity** — Binary rewards insufficient for complex trajectories
3. **Scaling RL to longer horizons** — Token-level optimization mismatches turn-structured interactions
4. **Generalization** — Tool-use training often overfits to training distributions
5. **Credit assignment** — Attributing success/failure to individual actions in multi-step tasks

## Identified Research Gaps (Publishable)

### Gap 1: RL for Agent Self-Repair
- T³ truncates bad trajectories, but no paper trains agents to *detect and recover from mid-execution failures*
- Train a repair policy via GRPO that observes execution traces and generates corrective actions

### Gap 2: Cross-Environment Transfer in RL-Trained Agents
- LaMer does in-context meta-RL, but no paper addresses transferring RL policies across fundamentally different environments (web → code → robotics) without retraining

### Gap 3: Curriculum RL for Progressive Agent Capability
- No paper applies curriculum learning to progressively harder multi-turn environments with automatic difficulty scheduling

### Gap 4: RL-based Agent Calibration (Know-When-to-Abstain)
- No paper trains agents via RL to know when to *refuse to act* or *ask for human clarification* based on uncertainty

### Gap 5: Scaling Laws for RL Post-Training Data
- All scaling law work focuses on pretraining/SFT. No paper derives scaling laws for RL training data (rollouts, diversity, model scale)
