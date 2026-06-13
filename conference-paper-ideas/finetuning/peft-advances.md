# Parameter-Efficient Fine-Tuning (PEFT) Advances — 2025-2026

## QLoRA Innovations

### QeRL (Quantization-enhanced RL) — arXiv:2510.xxxxx (Oct 2025)
- Combines NVFP4 quantization with LoRA to accelerate RL rollout
- Introduces **Adaptive Quantization Noise (AQN)** — quantization noise *helps* exploration by increasing policy entropy
- First framework to enable RL training of a 32B LLM on a single H100 80GB GPU
- 90.8% on GSM8K with a 7B model

### Ladder Up, Memory Down: Side Nets
- Lightweight side networks instead of adapter layers
- Cuts peak memory by **50% vs QLoRA**
- Enables fine-tuning 7B models on a single 12GB consumer GPU

### QLoRA + rsLoRA (Standard Practice 2025-2026)
- Now the default combination for resource-constrained fine-tuning
- Used in Nepali LLM adaptation (arXiv:2604.14171) at rank 32

## Beyond LoRA: New PEFT Methods

### DoRA: Weight-Decomposed Low-Rank Adaptation (arXiv:2402.09353)
- **ICML 2024 Oral**
- Decomposes pretrained weights into **magnitude** and **direction** components
- Applies LoRA only to directional updates
- Consistently outperforms LoRA on LLaMA, LLaVA
- No additional inference overhead
- Now adopted in production (e.g., Gazal-R1 combines DoRA + rsLoRA)

### LoRA+: Efficient Low Rank Adaptation (arXiv:2402.12354)
- Uses **different learning rates for A and B matrices** (standard LoRA uses the same, which is suboptimal)
- 1-2% performance improvement, up to **2× finetuning speedup**
- Zero extra compute cost

### rsLoRA: Rank-Stabilized LoRA (arXiv:2312.03732)
- Changes scaling factor from α/rank to **α/√rank**
- Fixes stunted learning at higher ranks
- Unlocks the compute/performance trade-off: higher ranks now give proportional gains
- Widely adopted in 2025-2026

### Other Notable Advances (2025)
| Method | Contribution |
|---|---|
| **Dual LoRA** | Separates matrices into magnitude (ReLU) and direction (sign); outperforms standard LoRA up to LLaMA-3 |
| **EffiLoRA** | Unified A matrix across layers + runtime selective B matrix updates |
| **PESO** | Unifying theoretical framework recovering LoRA with convergence guarantees |
| **SAILS** | Sparse Autoencoders for interpretable safety subspaces; 99.6% safety rate updating only 0.19% of parameters |
| **AdaGradSelect** | Adaptive gradient-guided layer selection; 12% faster, 35% less GPU memory, outperforms LoRA rank-256 by ~3% on GSM8K |

## Synthetic Data for Fine-Tuning

### AutoSynth
- Automates synthetic data workflow discovery via Monte Carlo Tree Search
- Reduces human effort by >90%

### "Synthetic Eggs in Many Baskets"
- Fine-tuning on synthetic data from **diverse sources mitigates distribution collapse**
- Preserves output diversity

### SPACE
- Self-play fine-tuning using noise contrastive estimation
- Stable convergence

### Domain-Specific Synthetic Data
- **QuantumChem-200K** (chemistry), **ATLAS** (2.7K verified Dafny programs), **ScrapeGraphAI-100k** (structured extraction)

### Risks
- **"When Bias Pretends to Be Truth"** — spurious correlations in synthetic data induce hallucinations immune to scaling
- **"When Tables Leak"** — tabular generators memorize and leak training data

## Key Insight
The PEFT toolkit is maturing: DoRA + LoRA+ + rsLoRA is now the standard production stack. The frontier has shifted from "can we fine-tune efficiently?" to "what data and curriculum should we fine-tune on?"

## Open Challenges
1. **Reward hacking in RL training** — models exploit verifier weaknesses
2. **Synthetic data quality assurance** — spurious correlations induce hallucinations
3. **Code model editing fragility** — edited code LLMs generalize poorly under successive edits
4. **Data contamination & memorization** — synthetic data generators leak training patterns
5. **Optimal data mixing remains empirical** — no principled theory for mixing ratios
