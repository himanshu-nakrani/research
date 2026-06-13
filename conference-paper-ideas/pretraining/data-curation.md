# Pretraining Data Curation & Mixing — Research Landscape (2025-2026)

## Key Papers

### MobileLLM-R1 (arXiv:2509.24945) — ICLR 2026
- Only **~2T tokens of high-quality curated data** sufficient (vs >10T typical)
- 950M model matches Qwen3-0.6B trained on 36T tokens
- Open-source with complete data mixing ratios
- **Key insight:** Quality >> Quantity

### AttentionInfluence (arXiv:2505.07293)
- Training-free data selection using small model's attention heads
- Selected 73B from 241B tokens with improved performance
- No additional training cost for data selection

### XDoGE
- Optimizes multilingual distribution using proxy model
- Balances high/mid/low-resource languages

### Scaling Laws with Vocabulary (arXiv:2407.13623) — NeurIPS 2024
- Optimal vocabulary size scales with compute
- Llama2-70B should have had 216K vocab (7× its 32K)
- Increasing 32K→43K improved ARC-Challenge from 29.1 to 32.0

### Data Mixing Laws — ICLR 2025
- Quantitative predictability of mixture proportions
- Enables principled mixing without exhaustive search

### Scaling Laws for Optimal Data Mixtures — 2026
- Universal method for optimal domain weights via scaling laws
- Predicts optimal mixture from small-scale experiments

## Data Selection Methods

### Quality Metrics
| Metric | Paper | Approach |
|---|---|---|
| Compression ratio | Beyond Random Sampling | Lower compression = easier |
| Lexical diversity (MTLD) | Beyond Random Sampling | Higher diversity = harder |
| Readability (Flesch) | Beyond Random Sampling | Simpler text = easier |
| Perplexity difference | PDPC | LLM's own difficulty assessment |
| Attention score | AttentionInfluence | Small model's attention patterns |

### Selection Strategies
1. **Rule-based filtering** — length, language, deduplication
2. **Model-based scoring** — perplexity, attention, classifier scores
3. **Curriculum ordering** — easy→hard scheduling
4. **Dynamic mixture** — adjusting weights during training

## Continual Pretraining (CPT)

### Key Papers
| Paper | Contribution |
|---|---|
| **ADEPT** | Selective layer expansion + decoupled tuning; outperforms full CPT with 15% of parameters |
| **SPEAR-MM** | Model merging preserves general capabilities; 91.2% retention vs 69.7% |
| **IKnow** | Self-supervised objectives as instruction-response dialogues for CPT |
| **Webscale-RL** | Converts pretraining docs into RL QA pairs; **100× more token-efficient** than CPT |
| **Curió-Edu 7B** | 10% of data + 20% compute outperforms full-corpus |
| **Emergent Abilities in CPT** | English data in multilingual CPT is critical for emergent capabilities |

### Key Findings
1. **Data selection > data volume** — 10% well-selected data can beat 100%
2. **Model merging helps** — preserves general capabilities during domain CPT
3. **RL conversion is highly efficient** — 100× more token-efficient than standard CPT
4. **English data enables emergence** — even in multilingual CPT, English is critical

## Identified Research Gaps

### Gap 1: Scaling Laws for Synthetic-Real Data Blends
- InfoLaw and ScalingLaws Revisited model real data quality/mixtures
- **No paper derives scaling laws for blended synthetic + real data pretraining**

### Gap 2: Data Curation for Agent-Specific Capabilities
- No paper studies what pretraining data composition best prepares models for agentic downstream tasks
- What data helps with tool use, multi-turn interaction, planning?

### Gap 3: Dynamic Data Mixture Scheduling
- Nanbeige4-3B uses fixed schedules
- **No paper learns optimal mixture schedules that change during training**
- e.g., more code early → more reasoning later → more tool-use data late

### Gap 4: Scaling Laws for Multi-Modal Pretraining Data
- Existing scaling laws focus on text
- No extension to multi-modal (text + image + code) pretraining mixtures

### Gap 5: Data Deduplication Scaling Laws
- No paper studies how deduplication effectiveness scales with corpus size
- How does it interact with model scale?

### Gap 6: Scaling Laws for RL Post-Training Data
- All scaling law work focuses on pretraining/finetuning
- **No paper derives scaling laws for RL training data** (rollouts, diversity, model scale)
