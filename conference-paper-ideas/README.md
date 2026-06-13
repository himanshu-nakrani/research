# Conference Paper Ideas — Research Exploration (June 2026)

Research topics explored for top/mid-tier AI/ML conferences, aligned with work in **LLM agents**, **fine-tuning**, and **pretraining**.

## Structure

```
conference-paper-ideas/
├── README.md                          # This file
├── conference-deadlines.md            # Upcoming deadlines
├── from-scratch-recommendations.md    # Realistic topics starting fresh
├── sauna-report-june-2026.md          # Sauna report: 3 trends (Agentic RAG, Multi-turn T2S, Eval)
├── agents/
│   ├── rl-for-agents.md               # RL training for LLM agents
│   ├── agent-memory.md                # Memory architectures
│   ├── agent-evaluation.md            # Benchmarks & reliability
│   └── multi-agent-systems.md         # Multi-agent collaboration
├── finetuning/
│   ├── peft-advances.md               # LoRA, DoRA, rsLoRA, QLoRA
│   ├── synthetic-data.md              # Synthetic data for fine-tuning
│   ├── reasoning-finetuning.md        # Fine-tuning for math/code/logic
│   └── curriculum-learning.md         # Curriculum learning for LLMs
└── pretraining/
    ├── data-curation.md               # Data mixing & selection
    ├── scaling-laws.md                # Scaling laws (including RL)
    └── continual-pretraining.md       # Domain adaptation
```

## Key Findings

- **RL >> SFT** for reasoning generalization (multiple 2025-2026 papers confirm)
- **How you train > how much you train** — data quality/selection beats data quantity
- **GRPO variants** dominating agent RL (Turn-PPO, SORL, Stratified GRPO, ASTER)
- **Memory architectures** moving toward hybrid episodic-semantic systems
- **Synthetic data** well-studied but lacks scaling law analysis for synthetic-real blends
- **Agent evaluation** lacks temporal reliability, cost-normalized, and adversarial testing

## Top Recommendations (From Scratch)

| Rank | Topic | Target | Timeline |
|---|---|---|---|
| 🥇 | Curriculum RL for Agent Tool-Use | ICLR 2027 | ~3 months |
| 🥈 | Synthetic Data Quality for Agents | AAAI 2027 | ~6 weeks |
| 🥉 | Adversarial Robustness of Tool-Using Agents | ICLR 2027 | ~3 months |
