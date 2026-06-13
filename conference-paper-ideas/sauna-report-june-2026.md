# Three Trends Shaping the LLM & Agentic AI Roadmap (June 2026)

> Source: [Sauna Report](https://app.sauna.ai/share/ai-research-trends-report-bzzmp4lrmbey)
> Synthesized from 100+ papers · Dec 2024 – June 2026
> Scoped to enterprise AI at State Street

---

## TL;DR

The research consensus is clear:
1. **Naive RAG is over** → replace with self-correcting, graph-guided agentic retrieval
2. **Single-prompt Text-to-SQL is deprecated** → replace with multi-turn spider-agents that self-correct against live schemas
3. **Vibe-check evaluation is dead** → replace with execution-based, agent-as-a-judge CI/CD pipelines

All three hit the current stack directly — Agent Forge, RAG pipelines, and Text-to-SQL engine.

---

## Trend 01: From Retrieval to Reasoning — The Agentic RAG Shift

Top-k vector retrieval can't survive production. High-citation papers converge on self-correction, graph structures, and inference-time verification.

### Key Papers

| Paper | Venue | Contribution |
|---|---|---|
| **Corrective RAG (CRAG)** | ICLR 2024 | Retrieval evaluator classifies chunks as Correct/Incorrect/Ambiguous. Fires web search when ambiguous, strips noise when incorrect. Significant hallucination reduction. |
| **GraphRAG** | Microsoft Research 2024 | Builds LLM-constructed entity knowledge graph with pre-generated community summaries. Handles corpus-wide queries ("what are the main compliance risks across 5,000 fund reports?") that standard RAG cannot. |
| **Self-Correcting RAG via MMKP + NLI-Guided MCTS** | arXiv 2026 | Formalizes context selection as Multi-dimensional Multiple-choice Knapsack Problem. Applies NLI-guided Monte Carlo Tree Search to verify reasoning paths at inference time. First paper to bring test-time search inside the RAG loop. |

### Evolution
```
Naive RAG:     Top-k → Generate (high hallucination)
CRAG:          Retrieval evaluator + adaptive search
GraphRAG:      Entity graph + global sensemaking
Agentic RAG:   MMKP pruning + NLI-MCTS verify (current frontier)
```

### State Street Implication
Fund administration, compliance review, and AUM reporting involve massive cross-document reasoning. A naive vector retrieval layer will fail exactly the queries that matter most — global risk roll-ups, cross-fund analytics, regulatory sensemaking.

### Roadmap
- Retrofit existing RAG pipelines with CRAG-style retrieval evaluator as quality gate
- Add GraphRAG layer for corpus-wide queries (fund reports, compliance docs, investment research)
- MCTS-based inference-time verification as optional reasoning mode for high-stakes agents in Agent Forge

---

## Trend 02: Single-Prompt Text-to-SQL Is Deprecated

Real enterprise databases with 1,000+ columns, multi-turn ambiguity, and dialect complexity have killed single-shot SQL generation.

### Key Papers

| Paper | Venue | Contribution |
|---|---|---|
| **BIRD-SQL** | NeurIPS 2024 | 33.4 GB across 95 databases with noisy real-world data. Introduced Valid Efficiency Score (VES) — measures correctness AND execution performance. Exposed that SOTA models struggle with messy values. |
| **Spider 2.0** | ICLR 2025 | 632 real enterprise problems from Snowflake/BigQuery, often 1,000+ column schemas. Best single-prompt model scores ~17% — single-prompt Text-to-SQL is non-viable at enterprise scale. |
| **BIRD-Interact** | arXiv 2025 | Interactive user simulator testing multi-turn ambiguity handling, clarifying questions, schema exploration, error recovery, and CRUD operations. First benchmark evaluating the full conversational loop. |

### Evolution
```
Before (deprecated):  User Question → Single Prompt → SQL
After (current):      User Question + Ambiguities → Schema Inspection + Clarify → Execute in Sandbox → Self-Correct on Error → Verified SQL Result
```

### State Street Implication
Alpha platform likely has schemas in the 1,000+ column territory — fund NAV tables, position records, transaction history. Spider 2.0's 17% single-prompt accuracy should end illusions about single-shot Text-to-SQL surviving in production.

### Roadmap
- Replace Text-to-SQL engine with agentic spider-agent (inspect schemas, execute in sandbox, catch errors, retry)
- Add VES metric to evaluation suite — SQL correctness alone is insufficient; query execution cost matters
- Build BIRD-Interact style interactive simulator into Agent Forge for multi-turn disambiguation testing

---

## Trend 03: Execution-Based, Agent-as-a-Judge Evaluation in CI/CD

Static benchmark era is over. The papers that matter now test agents in live sandboxes, measure execution outcomes, and use other agents to score intermediate steps.

### Key Papers

| Paper | Venue | Contribution |
|---|---|---|
| **SWE-bench** | ICLR 2024 Oral | Tasks models with generating executable code patches for real GitHub issues. Execution is the judge — patch either passes test suite or it doesn't. No ambiguity. Evolved into SWE-bench Verified and Multimodal. |
| **Agent-as-a-Judge** | arXiv 2024 | Multi-agent framework judging code-generating agents on intermediate execution steps, not just final outputs. 90% alignment with human experts, 97.6% cost reduction. Judge sees full trace — tool calls, errors, intermediate state. |
| **GAIA2** | 2026 | Successor to GAIA. Evaluates agents in fully async environments — emails, calendars, messaging. Real state-change verification. If agent says it sent an email, evaluator checks the mailbox. |

### Evolution
```
Before:  Static gold-standard datasets → LLM judge on final output → Manual human review
After:   Live sandboxed execution → Agent-as-judge on full trace → CI/CD automated gate
```

### State Street Implication
At State Street's risk tolerance, shipping an agent that hasn't passed a live sandbox evaluation suite is unacceptable.

### Proposed Agent Forge Eval Pipeline
```
Agent Deployment → Live Sandbox (execute tasks/tools) → Agent-as-a-Judge (score full trace) → State Verification (did the world change?) → PASS/FAIL
```

### Roadmap
- Move from static datasets to live sandboxed execution environments (Docker-containerized task runners)
- Implement Agent-as-a-Judge for trace-level scoring (every tool call, error, retry, intermediate state)
- Wire Agent Forge into CI/CD as deployment gate — no agent ships without passing eval suite
- Add adversarial eval passes: prompt injection attempts, schema hallucination probes, compliance-sensitive edge cases

---

## Source Papers

### RAG
- Yan et al. — "Corrective Retrieval Augmented Generation (CRAG)" · ICLR 2024
- Edge et al. — "From Local to Global: A GraphRAG Approach to Query-Focused Summarization" · Microsoft Research 2024
- "Self-Correcting RAG: Enhancing Faithfulness via MMKP Context Selection and NLI-Guided MCTS" · arXiv 2026

### SQL
- Li et al. — "BIRD-SQL: Can LLM Already Serve as A Database Interface?" · NeurIPS 2024
- Lei et al. — "Spider 2.0: Evaluating Language Models on Real-World Enterprise Text-to-SQL Workflows" · ICLR 2025
- "BIRD-Interact: Re-imagining Text-to-SQL Evaluation via Dynamic Interactions" · arXiv 2025

### Eval
- Jimenez et al. — "SWE-bench: Can Language Models Resolve Real-World GitHub Issues?" · ICLR 2024 Oral
- Zhuge et al. — "Agent-as-a-Judge: Evaluate Agents with Agents" · arXiv 2024
- Mialon et al. — "GAIA: A Benchmark for General AI Assistants" · ICLR 2024 / Meta AI
- "GAIA2: Agents in Asynchronous Real-World Environments" · 2026

### Agents
- Wu et al. — "AutoGen: Enabling Next-Gen LLM Applications" · COLM 2024
- "Towards a Science of Scaling Agent Systems" · arXiv 2025

### LLMs
- Morris et al. — "Levels of AGI for Operationalizing Progress on the Path to AGI" · ICML 2024
- Wang et al. — "MMLU-Pro: A More Robust and Challenging Multi-Task Language Understanding Benchmark" · NeurIPS 2024
