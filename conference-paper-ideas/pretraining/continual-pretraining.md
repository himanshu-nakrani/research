# Continual Pretraining — Research Landscape (2025-2026)

## Key Methods

### ADEPT
- Selective layer expansion + decoupled tuning
- Outperforms full-parameter CPT with only **15% of parameters**
- Efficient domain adaptation without catastrophic forgetting

### SPEAR-MM
- Model merging to preserve general capabilities during domain CPT
- **91.2% retention** vs 69.7% for standard CPT
- Merges domain-adapted and general-purpose models

### IKnow
- Self-supervised objectives formatted as instruction-response dialogues
- Enables CPT of instruction-tuned models (not just base models)
- Bridges the gap between pretraining and instruction-following

### Webscale-RL
- Converts pretraining documents into RL QA pairs
- RL training is **100× more token-efficient** than CPT for similar performance
- Paradigm shift: don't just continue pretraining, convert to RL

### Curió-Edu 7B
- Data selection more important than volume
- **10% of data + 20% compute outperforms full-corpus model**
- Quality curation is the key lever

### Emergent Abilities in CPT (arXiv:2506.00288)
- English data in multilingual CPT is critical for emergent capabilities
- Even if it doesn't improve perplexity, it enables new abilities
- Implication: don't remove English from multilingual CPT

## Key Findings

1. **Selective adaptation > full fine-tuning** — ADEPT shows 15% of parameters is sufficient
2. **Model merging prevents forgetting** — SPEAR-MM achieves 91.2% retention
3. **RL conversion is dramatically more efficient** — 100× token efficiency with Webscale-RL
4. **Data curation is the primary lever** — 10% well-curated data beats 100% uncurated
5. **English enables emergence** — Critical for multilingual models even without direct perplexity improvement

## CPT Challenges

### Catastrophic Forgetting
- Standard CPT causes significant capability loss on general tasks
- Best mitigation: SPEAR-MM (91.2% retention)
- Still loses ~9% — no perfect solution

### Domain Interference
- CPT on one domain can hurt performance on related domains
- No principled method to predict interference patterns

### Evaluation
- How to measure "what was lost" during CPT?
- Need both domain-specific and general benchmarks

## Practical CPT Pipeline (2026 Best Practice)

```
1. Data Curation
   └── Select 10-20% highest quality domain data
   └── Include 5-10% English for emergence

2. Training Strategy
   └── Option A: ADEPT (selective layers, 15% params)
   └── Option B: Full CPT with SPEAR-MM merging
   └── Option C: Webscale-RL conversion (most efficient)

3. Forgetting Prevention
   └── Replay 1% of original pretraining data
   └── Or: Train domain model → merge with general model

4. Evaluation
   └── Domain benchmarks (in-distribution)
   └── General benchmarks (catastrophic forgetting)
   └── Emergent capability probes
```

## Identified Research Gaps

1. **Optimal replay buffer sizing** — 1% is heuristically chosen; no scaling law
2. **Domain interference prediction** — Can we predict which domains will interfere?
3. **CPT curriculum design** — What order to introduce domain data?
4. **Multi-domain CPT** — Simultaneous adaptation to multiple domains
5. **CPT for agent capabilities** — No paper studies CPT specifically for tool-use/planning
6. **Webscale-RL for domains** — Converting domain-specific documents to RL tasks
