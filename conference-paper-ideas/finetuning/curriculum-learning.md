# Curriculum Learning for LLMs — Research Landscape (2025-2026)

## Key Findings

### "Beyond Random Sampling" (arXiv:2506.11300)
- Systematic evaluation across 200+ models
- CL **accelerates convergence by 18-45%** in early/mid-training
- Best difficulty metrics: compression ratio, lexical diversity (MTLD), readability (Flesch)
- As warmup, yields sustained 3.5% improvements

### Preference Curriculum / PDPC (arXiv:2501.13126)
- LLMs' data preferences change dynamically during training
- Uses perplexity difference metric to schedule data
- 3B model trained with PDPC on 1T tokens achieves **+8.1% average accuracy on MMLU/CMMLU**

### ACER: Automated Curriculum-Enhanced Regimen (arXiv:2510.26336)
- Generates synthetic textbook curricula using Bloom's taxonomy for continual pretraining
- Boosts accuracy by 5pp in challenging domains

### Vocabulary Curriculum Learning (arXiv:2502.17910)
- Dynamic tokenization during pretraining with entropy-guided vocabulary expansion
- Shows log-linear scaling gains relative to vocabulary size

### Learning Rate Decay Incompatibility (arXiv:2511.18903)
- Standard LR decay **diminishes benefits** of curriculum pretraining
- Fix: moderate LR decay or replace with model averaging
- Combined improvement: +1.64% over random shuffling

### Reasoning Curriculum (arXiv:2510.26143)
- Two-stage: math-only RL first (skill elicitation), then joint multi-domain RL (transfer)
- Consistent gains on Qwen3-4B and Llama-3.1-8B

## Key Insights
1. **CL works but requires careful LR scheduling** — standard LR decay undermines CL benefits
2. **Dynamic preferences matter** — what data is useful changes during training
3. **Bloom's taxonomy provides a useful framework** — easy→hard ordering aligns with educational theory
4. **Vocabulary curriculum is underexplored** — dynamic tokenization shows promise

## Open Challenges
1. **LR schedule × curriculum interaction** — optimal scheduling remains open
2. **Automatic difficulty scoring** — no universal metric for "how hard is this example?"
3. **Curriculum for RL training** — no paper applies curriculum to RL agent training
4. **Multi-domain curriculum** — how to order data across different domains (math, code, language)
5. **Curriculum for synthetic data** — ordering generated data by difficulty

## Identified Research Gaps
- **Curriculum RL for LLM agents** — no paper applies CL to progressively harder multi-turn environments
- **Adaptive curriculum** — adjusting difficulty based on real-time model performance
- **Cross-domain curriculum transfer** — does curriculum learned on one domain help another?
- **Curriculum for synthetic data generation** — generating data in difficulty order
