# Synthetic Data for Fine-Tuning — Research Landscape (2025-2026)

## Current State

### Generation Methods
| Paper | Method | Scale |
|---|---|---|
| **AutoSynth** | Monte Carlo Tree Search for workflow discovery | >90% human effort reduction |
| **SPARQ** | Quality-diversity algorithms for math QA | 20M+ pairs |
| **CodeEvo** | Coder-Reviewer iterative code synthesis | Multi-round refinement |
| **GenesisFunc** | Multi-agent framework for function-calling dialogues | Agent tool-use data |
| **ToolMind** | Multi-agent simulation for tool-use | 160k instances |
| **SING-SQL** | Auto-generated Text-to-SQL for any target database | Database-specific |
| **UPDESH** | Culturally-grounded synthetic instructions | 9.5M, 13 Indian languages |
| **EmbGen** | Entity-description decomposition for diverse QA | Structured diversity |

### Quality vs. Quantity
- **"Synthetic Eggs in Many Baskets"** — Diverse sources mitigate distribution collapse
- **MobileLLM-R1** (ICLR 2026) — Only ~2T tokens of high-quality curated data sufficient (vs >10T typical)
- **Curió-Edu 7B** — 10% of data + 20% compute outperforms full-corpus model

### Risks
- **"When Bias Pretends to Be Truth"** — Spurious correlations induce hallucinations immune to scaling
- **"When Tables Leak"** — Synthetic generators memorize and leak training data
- **NodeSynth** — Synthetic social queries show 5× failure rate on evaluation

## Identified Research Gaps (Publishable)

### Gap 1: Scaling Laws for Synthetic-Real Data Blends ⭐
- ScalingLaws Revisited (ICLR 2026) introduces quality parameter Q for real data
- **No paper extends scaling laws to synthetic data specifically**
- How much synthetic data is optimal vs. real data at what quality?
- Train models at 1B, 3B, 7B scales with varying synthetic:real ratios

### Gap 2: Synthetic Data Contamination Detection
- No paper addresses how to detect when synthetic training data has been contaminated by the evaluation benchmark
- Creates circular evaluation — models trained on data that includes test answers

### Gap 3: Adversarial Synthetic Data for Robustness
- NodeSynth generates evaluation data
- **No paper generates adversarial synthetic training data to improve agent robustness under distribution shift**

### Gap 4: Synthetic Data for Multi-Modal Agent Trajectories
- All synthetic data work focuses on text
- **No paper synthesizes multi-modal (text + screenshot + action) agent trajectories** for GUI/web agents

### Gap 5: Automatic Synthetic Data Curriculum Design
- SPARQ generates math problems
- **No paper automatically designs curriculum ordering** of synthetic data from easy→hard tailored to a model's current capabilities

### Gap 6: Synthetic Data Budget Allocation Across Domains
- No paper addresses optimal allocation of a fixed synthetic data budget across multiple target domains (code + math + tool-use + reasoning simultaneously)

## Practical Considerations

### Cost
- Generating 100k synthetic trajectories via GPT-4o: ~$50-200 depending on complexity
- Local generation with Qwen2.5-72B (vLLM): ~$10-30 in compute
- Quality filtering + deduplication: adds ~20-30% to generation cost

### Evaluation
- Standard benchmarks: ToolBench, API-Bank, SWE-bench, GAIA
- Novel evaluation: diversity metrics, contamination detection, downstream task correlation

### Key Insight
The field is converging on **quality > quantity** for synthetic data. The frontier is shifting from "how to generate synthetic data" to "how to generate the right synthetic data in the right order."
