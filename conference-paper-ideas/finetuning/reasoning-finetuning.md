# Fine-Tuning for Reasoning — Research Landscape (2025-2026)

## RL-Based Reasoning (Dominant Paradigm)

### Key Results
| Paper | Model | AIME 2024 | AIME 2025 | Method |
|---|---|---|---|---|
| **PCL-Reasoner-V1.5** | Qwen2.5-32B | 90.9% | 85.6% | SFT + offline RL |
| **Parallel-R1** | — | — | +42.9% vs baseline | First RL for parallel thinking |
| **SimpleTIR** | Qwen2.5-7B | 50.5 (from 22.1) | — | Multi-turn tool-integrated RL |
| **ASTER-4B** | — | — | 90.0% | Tool-augmented RL |
| **SPARK** | — | +9.7% avg | — | Recycles rollout data as reward model |

### Key Insight: RL >> SFT for Reasoning Generalization
Multiple papers confirm that RL-based training generalizes better than SFT for reasoning tasks. SFT useful primarily for "cold start."

### Dynamic Fine-Tuning (DFT)
- Dynamically rescales gradient updates with token probability
- Single-line code change outperforms SFT on math, code, multimodal tasks

### DELTA-Code (arXiv:2509.21016)
- Probes RL for learning new reasoning strategies
- Key finding: RL exhibits **"grokking phase transition"** — models abruptly achieve near-perfect accuracy after extended near-zero reward

## QLoRA Fine-Tuning for Math Reasoning

### LLaMA 3.2-3B Math Reasoning
- **Method:** QLoRA on 200 synthetic samples generated on AMD MI300X
- **Adapter:** 46 MB, 0.47% trainable params
- **Results:**
  - 77% loss reduction
  - 90% token accuracy
  - 32 min training time on NVIDIA A10G
- **Model:** [Hugging Face](https://huggingface.co/himanshunakrani9/llama-3.2-3b-reasoning-sft)

### TinyMathReason-1B (From-Scratch Pretraining)
- **Architecture:** LLaMA-style (22 layers, 2048 hidden, 16Q/4KV heads)
- **Tokenizer:** Custom 32k
- **Training:** TPU v4-64 using MaxText
- **Results:**
  - 1.07B parameters
  - 57B tokens trained
  - 54,363 training steps (~1M tokens/step)

## Process Reward Models

### AdaptiveStep (ICML 2025, arXiv:2502.13943)
- Divides reasoning steps by model confidence rather than rule-based heuristics
- 30% cost reduction in PRM construction
- SOTA Best-of-N performance

### STAR-PólyaMath
- Persistent meta-strategic supervision
- Perfect scores on AIME, Putnam, HMMT

## Reasoning Curriculum

### Two-Stage Curriculum (arXiv:2510.26143)
- Stage 1: Math-only RL (skill elicitation)
- Stage 2: Joint multi-domain RL (transfer)
- Consistent gains on Qwen3-4B and Llama-3.1-8B

### Key Insight
Curriculum ordering matters: math-first → multi-domain transfer works better than joint training from the start.

## Open Challenges
1. **Reward hacking** — Models exploit verifier weaknesses rather than genuinely reason
2. **Scaling RL reasoning to general domains** — Works well for math/code with verifiable rewards; extending to subjective tasks is unsolved
3. **Grokking dynamics** — Phase transitions are unpredictable; no principled way to trigger them
4. **Process vs. outcome rewards** — Process rewards are expensive; outcome rewards are sparse
5. **Multi-domain transfer** — Reasoning skills from math don't always transfer to code/science

## Identified Research Gaps
- **Lightweight PRM construction** using synthetic reasoning traces from small models
- **Curriculum RL for reasoning** with automatic difficulty scheduling
- **Cross-domain reasoning transfer** — formalize when and how reasoning skills transfer
- **Grokking prediction** — can we predict/trigger the phase transition?
