# From-Scratch Research Recommendations

Topics evaluated for feasibility starting from zero — no existing data, no existing infrastructure, just open-source tools and models.

## AAAI 2027 (~6 weeks, deadline Jul 28, 2026)

### A. Benchmark Paper: PEFT Methods for Agent Tasks
- **What:** Compare DoRA, LoRA+, rsLoRA, QLoRA on existing agent benchmarks (GAIA, SWE-bench, ToolBench) using open models (Qwen, LLaMA).
- **Contribution:** Systematic analysis of cost vs. performance for PEFT in agent contexts.
- **Effort:** ⭐⭐ Doable
- **Models:** Qwen2.5-7B, LLaMA-3.1-8B
- **Data:** Existing benchmarks (no data collection needed)

### B. Analysis: When Do Agents Fail? A Taxonomy from Public Traces
- **What:** Collect failure traces from public agent runs (SWE-bench submissions, open agent frameworks). Build a failure taxonomy + detection heuristics.
- **Contribution:** First systematic failure analysis from public data.
- **Effort:** ⭐⭐ Doable
- **Data:** Public SWE-bench traces, AgentBench, GAIA submissions

### C. Synthetic Data Quality: What Makes Agent Training Data Work? ⭐ RECOMMENDED
- **What:** Generate synthetic agent trajectories with varying properties (diversity, difficulty, error types). Measure what data characteristics correlate with downstream performance.
- **Contribution:** Principled guidelines for synthetic agent data generation.
- **Effort:** ⭐⭐⭐ Ambitious but possible
- **Models:** GPT-4o / Qwen2.5 for generation, Qwen2.5-3B for evaluation
- **Data:** Generate via API, evaluate on ToolBench / API-Bank

## ICLR 2027 (~3 months, deadline ~Sep 2026)

### D. Curriculum RL for Agent Tool-Use ⭐ TOP PICK
- **What:** Progressive difficulty scheduling for RL-trained agents. Start with simple single-tool tasks → multi-tool → complex planning. Use GRPO + automatic difficulty scoring.
- **Contribution:** First curriculum learning framework for LLM agent RL. Show faster convergence and better generalization.
- **Effort:** ⭐⭐⭐ Strong
- **Models:** Qwen2.5-1.5B/3B (trainable on 1-2 GPUs)
- **Frameworks:** HuggingFace TRL (GRPO), ToolBench, API-Bank
- **Key Innovation:** Automatic difficulty scorer for agent environments + progressive training schedule

### E. RL for Agent Self-Repair
- **What:** Train agents on SWE-bench or similar, inject failures mid-execution, train a repair policy via RL. Show recovery rate improvements.
- **Contribution:** First RL-trained self-repair mechanism for LLM agents.
- **Effort:** ⭐⭐⭐ Strong
- **Models:** Qwen2.5-3B/7B
- **Data:** SWE-bench + synthetic failure injection

### F. Scaling Laws for RL Agent Training
- **What:** Train 1B, 3B, 7B models with varying RL rollout counts on tool-use tasks. Fit scaling laws for RL post-training.
- **Contribution:** First scaling law analysis for RL agent training data.
- **Effort:** ⭐⭐⭐ Needs compute (multiple training runs)
- **Models:** Qwen2.5-1.5B, 3B, 7B
- **Compute:** ~50-100 GPU hours

### G. Synthetic Data for Multi-Step Reasoning Agents
- **What:** Generate synthetic multi-step reasoning traces (tool calls, planning, error recovery). Fine-tune and evaluate on agent benchmarks.
- **Contribution:** Novel synthetic data pipeline for agent capabilities.
- **Effort:** ⭐⭐ Feasible
- **Models:** GPT-4o for generation, Qwen2.5-3B for fine-tuning

### H. Adversarial Robustness of Tool-Using Agents ⭐ RECOMMENDED
- **What:** Generate adversarial tool responses (wrong outputs, misleading errors). Train agents with adversarial augmentation. Measure robustness gains.
- **Contribution:** First systematic adversarial robustness framework for tool-using agents.
- **Effort:** ⭐⭐⭐ Novel
- **Models:** Qwen2.5-3B/7B
- **Data:** Generate adversarial tool responses programmatically
- **Evaluation:** WAREX, MCPAgentBench, custom adversarial suite

## Minimal Setup Needed

### Hardware
- **GPU:** 1x A100/H100 (cloud ~$1-2/hr on Lambda/RunPod)
- **Storage:** ~100GB for models + data

### Software Stack
- **Training:** HuggingFace TRL (GRPO), PEFT, Unsloth (fast LoRA)
- **Inference:** vLLM
- **Benchmarks:** ToolBench, API-Bank, SWE-bench, GAIA
- **Models:** Qwen2.5 series (1.5B-7B), LLaMA-3.1-8B
- **Data Generation:** OpenAI API, Qwen2.5-72B (local/vLLM)

### Estimated Compute Cost
| Topic | GPU Hours | Est. Cost |
|---|---|---|
| A (PEFT Benchmark) | ~20 hrs | $40-60 |
| B (Failure Taxonomy) | ~5 hrs | $10-15 |
| C (Synthetic Data Quality) | ~30 hrs | $60-90 |
| D (Curriculum RL) | ~80 hrs | $160-240 |
| E (Self-Repair RL) | ~60 hrs | $120-180 |
| F (Scaling Laws) | ~150 hrs | $300-450 |
| G (Synthetic Reasoning) | ~40 hrs | $80-120 |
| H (Adversarial Robustness) | ~50 hrs | $100-150 |
