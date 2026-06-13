# Scaling Laws — Research Landscape (2025-2026)

## Established Scaling Laws

### Chinchilla (Hoffmann et al., 2022)
- Optimal tokens ≈ 20× model parameters
- Foundation for modern training budgets

### ScalingLaws Revisited (ICLR 2026)
- Introduces **quality parameter Q** for real data
- Extends Chinchilla with data quality dimension
- Higher quality data → fewer tokens needed

### InfoLaw (ICML 2026)
- Data-aware scaling framework
- Models mixture weights + repetition effects
- Predicts optimal data composition

### Data Mixing Laws (ICLR 2025)
- Quantitative predictability of mixture proportions
- Enables principled mixing without exhaustive search

### Scaling Laws for Optimal Data Mixtures (2026)
- Universal method for optimal domain weights
- Predicts optimal mixture from small-scale experiments

### Scaling Laws with Vocabulary (NeurIPS 2024)
- Optimal vocabulary size scales with compute
- Llama2-70B should have had 216K vocab (7× its 32K)

### Scaling Laws for Forgetting during Finetuning (2026)
- 1% pretraining data prevents catastrophic forgetting
- Quantifies the forgetting-prevention tradeoff

## Novel Scaling Law Directions

### Scaling Laws for Synthetic-Real Data Blends ⭐
- **Gap:** No paper derives scaling laws for blended synthetic + real data
- **Question:** What ratio of synthetic to real is optimal at different scales?
- **Approach:** Train at 1B, 3B, 7B with varying ratios, fit parameters

### Scaling Laws for RL Post-Training Data ⭐
- **Gap:** All scaling law work focuses on pretraining/SFT
- **Question:** How many RL rollouts, what diversity, at what model scale?
- **Approach:** Train 1B-8B with varying rollout counts, fit scaling laws

### Scaling Laws for Multi-Modal Pretraining
- **Gap:** Existing laws focus on text only
- **Question:** How do text + image + code mixtures scale?
- **Approach:** Multi-modal training at different scales and mixtures

### Data Deduplication Scaling Laws
- **Gap:** No systematic study of dedup effectiveness vs. corpus/model scale
- **Question:** How does dedup interact with model scale?
- **Approach:** Vary dedup aggressiveness, measure at different scales

## Key Insights
1. **Quality > Quantity** — MobileLLM-R1: 2T high-quality tokens beat 36T tokens
2. **Vocabulary matters more than expected** — Optimal vocab scales with compute
3. **Forgetting is predictable** — 1% pretraining data prevents it
4. **Mixtures are predictable** — Small-scale experiments predict large-scale optima

## Practical Implications
- **Budget allocation:** Spend compute on data quality, not just more data
- **Vocabulary sizing:** Scale vocab with model size
- **CPT strategy:** Use model merging (SPEAR-MM) + small replay buffer
- **RL training:** No established scaling laws yet — frontier research opportunity
