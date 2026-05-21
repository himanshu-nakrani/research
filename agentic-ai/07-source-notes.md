# 07 — Source Notes

Last updated: 2026-05-22 IST

This file lists the main sources used for the research pack and the key facts extracted from each. Links are included so the guide can be refreshed later.

## Strategy, adoption, and enterprise reports

### McKinsey — The state of AI in 2025: Agents, innovation, and transformation

URL: https://www.mckinsey.com.br/capabilities/quantumblack/our-insights/the-state-of-ai

Key points used:

- 88% of respondents report regular AI use in at least one business function.
- 62% say their organizations are at least experimenting with AI agents.
- 23% are scaling an agentic AI system somewhere in the enterprise.
- In any given function, no more than 10% report scaling agents.
- IT and knowledge management are leading agentic use cases.
- Workflow redesign is a key success factor.

### McKinsey — The agentic organization

URL: https://www.mckinsey.com/capabilities/people-and-organizational-performance/our-insights/the-agentic-organization-contours-of-the-next-paradigm-for-the-ai-era

Key points used:

- Frames the "agentic organization" as humans, virtual agents, and physical agents working together.
- Claims task length AI can reliably complete has doubled roughly every seven months since 2019 and every four months since 2024.
- Emphasizes business model, operating model, governance, workforce/culture, and technology/data pillars.

### Deloitte — The agentic reality check

URL: https://www.deloitte.com/us/en/insights/topics/technology-management/tech-trends/2026/agentic-ai-strategy.html

Key points used:

- Gartner prediction quoted by Deloitte: 15% of day-to-day work decisions made autonomously by agentic AI by 2028; 33% of enterprise software applications include agentic AI by 2028.
- Deloitte survey: 30% exploring, 38% piloting, 14% ready to deploy, 11% in production.
- Key blockers: legacy integration, data architecture, governance/control frameworks.

### Accenture — Six key insights for C-suite executives to maximize return on agentic AI

URL: https://www.accenture.com/content/dam/accenture/final/accenture-com/document-4/Accenture-Six-Key-Insights-for-C-suite-Executives-to-Maximize-Return-on-Agentic-AI.pdf

Key points used:

- Agentic AI as a new economic resource/digital labor.
- Examples of document-processing and marketing-agent transformations.
- Emphasis on enterprise knowledge brain, data usability, governance, and continuous improvement.

### State of AI Report 2025

URL: https://www.stateof.ai/

Key points used:

- Reasoning defined the year; models can plan, reflect, self-correct, and work over longer horizons.
- Commercial traction accelerated; AI adoption mainstreamed.
- Safety focus is shifting toward reliability, cyber resilience, and governance of autonomous systems.

### MIT — 2025 AI Agent Index

URL: https://aiagentindex.mit.edu/

Key points used:

- 24/30 prominent agents were released or received major updates in 2024-2025.
- Browser agents often operate at higher autonomy levels than chat agents.
- Safety disclosure lags capability disclosure.
- Many agents rely on GPT, Claude, or Gemini families; structural dependency risk.

## Product and platform sources

### OpenAI — Computer-Using Agent

URL: https://openai.com/index/computer-using-agent/

Key points used:

- CUA combines GPT-4o vision with reasoning/RL for GUI interaction.
- Reported scores: OSWorld 38.1%, WebArena 58.1%, WebVoyager 87%.
- Uses screenshot perception, reasoning, and mouse/keyboard actions.
- Human confirmation for sensitive actions.

### OpenAI — Introducing ChatGPT agent

URL: https://openai.com/index/introducing-chatgpt-agent/

Key points used:

- Unified agentic system combining Operator web interaction, deep research synthesis, and ChatGPT conversation.
- Tools include visual browser, text browser, terminal, direct API access, and connectors.
- Users can interrupt, steer, or take over.

### OpenAI Agents SDK

URL: https://openai.github.io/openai-agents-python/

Key points used:

- Primitives: agents, handoffs/agents-as-tools, guardrails.
- Features: agent loop, sandbox agents, sessions, human-in-loop, tracing, MCP support.

### Anthropic — How we built our multi-agent research system

URL: https://www.anthropic.com/engineering/multi-agent-research-system

Key points used:

- Orchestrator-worker multi-agent architecture for research.
- Multi-agent system with Claude Opus 4 lead and Claude Sonnet 4 subagents outperformed single-agent Claude Opus 4 by 90.2% on internal eval.
- Agents use about 4x tokens vs chat; multi-agent about 15x tokens vs chat.
- Token usage explained much of performance variance in BrowseComp analysis.

### Anthropic — Building agents with the Claude Agent SDK

URL: https://www.anthropic.com/engineering/building-agents-with-the-claude-agent-sdk

Key points used:

- Claude Code harness generalized to Claude Agent SDK.
- Design principle: give agents a computer.
- Agent loop: gather context -> take action -> verify work -> repeat.
- Useful for finance, personal assistant, support, and deep research agents.

### Google — Gemini as a universal AI assistant

URL: https://blog.google/innovation-and-ai/models-and-research/google-deepmind/gemini-universal-ai-assistant/

Key points used:

- Gemini as a world model and universal AI assistant.
- Project Astra: video understanding, screen sharing, memory.
- Project Mariner: browser agents, up to ten tasks at a time.
- Computer-use capabilities moving into Gemini API.

## Benchmarks and research papers

### SWE-bench paper

URL: https://proceedings.iclr.cc/paper_files/paper/2024/file/edac78c3e300629acfe6cbe9ca88fb84-Paper-Conference.pdf

Key points used:

- 2,294 real GitHub issue tasks.
- Original baseline: Claude 2 solved 1.96% with BM25 retrieval.
- Establishes real repository-level software engineering as a hard benchmark.

### SWE-bench official leaderboard

URL: https://www.swebench.com/verified

Key points used:

- SWE-bench Verified is a human-filtered 500-instance subset.
- Leaderboard distinguishes full agent systems and mini-SWE-agent LM comparisons.
- Harness and scaffold matter.

### WebArena paper/site

URLs:

- https://proceedings.iclr.cc/paper_files/paper/2024/file/4410c0711e9154a7a2d26f9b3816d1ef-Paper-Conference.pdf
- https://webarena.dev/og/

Key points used:

- Realistic self-hosted web environments.
- Original best GPT-4-based agent: 14.41% task success.
- Human performance: 78.24%.

### WorkArena

URL: https://arxiv.org/html/2403.07718

Key points used:

- Enterprise software benchmark based on ServiceNow.
- 33 tasks and 19,912 unique instances.
- GPT-4o reported 43% success in extracted content.
- Highlights enterprise UI automation gap.

### AssistantBench

URL: https://aclanthology.org/anthology-files/anthology-files/pdf/emnlp/2024.emnlp-main.505.pdf

Key points used:

- 214 realistic time-consuming web tasks.
- No model reached more than 25 points.
- Open-web navigation remains difficult.

### tau-bench

URL: https://github.com/sierra-research/tau-bench

Key points used:

- Tool-agent-user interaction benchmark for airline and retail.
- Repository warns old tasks are outdated and points to tau2/tau3-bench.
- Historical leaderboard numbers used with caution.

### Agentic Benchmark Checklist paper

URL: https://arxiv.org/html/2507.02825v5

Key points used:

- Many agentic benchmarks have task or outcome validity flaws.
- Flaws can over/underestimate performance by up to 100% relative.
- Examples: SWE-bench-Verified insufficient tests, tau-bench empty responses.
- Introduces Agentic Benchmark Checklist.

### AgentRewardBench

URL: https://arxiv.org/pdf/2504.08942

Key points used:

- Evaluates LLM judges for web-agent trajectories.
- 1,302 trajectories across 5 benchmarks and 4 LLMs.
- Rule-based evaluation may underreport success and diverge from expert judgment.

## Security and governance sources

### OWASP — State of Agentic AI Security and Governance

URL: https://genai.owasp.org/download/50592/?tmstv=1754459367

Key points used:

- Agentic AI introduces a new threat surface: autonomy, memory, reasoning, tool access.
- Risks include memory poisoning, tool misuse, prompt injection, insider threats.
- Recommends defense in depth across lifecycle, fine-grained access control, runtime monitoring, governance.

### Design Patterns for Securing LLM Agents against Prompt Injections

URL: https://arxiv.org/html/2506.08837v2

Key points used:

- Prompt injection is especially dangerous when agents have tools or sensitive data.
- Proposed design patterns constrain agents to improve resistance.
- Key idea: after ingesting untrusted input, prevent it from triggering consequential actions.
- Plan-then-execute as a control-flow-integrity-like pattern.

### EchoLeak paper

URL: https://arxiv.org/html/2509.10540

Key points used:

- Case study of CVE-2025-32711 in Microsoft 365 Copilot.
- Zero-click prompt injection through crafted email causing data exfiltration.
- Defenses: prompt partitioning, input/output filtering, provenance-based access control, strict CSP, adversarial testing.

### TRiSM for Agentic AI

URL: https://arxiv.org/html/2506.04133v4

Key points used:

- Agentic multi-agent systems need trust, risk, security management.
- Risks include coordination failures, prompt manipulation, memory poisoning, tool abuse, privacy leakage.

### From Prompt Injections to Protocol Exploits

URL: https://arxiv.org/pdf/2506.23260v1

Key points used:

- Threat model for LLM-agent ecosystems spanning host-to-tool and agent-to-agent communications.
- Categories include input manipulation, model compromise, system/privacy attacks, protocol vulnerabilities.

## Notes on confidence

High confidence:

- Agentic adoption is broad but production scaling is early.
- Coding agents are the most mature category.
- Security and governance are central blockers.
- Benchmarks must be interpreted carefully because scaffolds and evaluation designs matter.

Medium confidence:

- Specific leaderboard numbers, because they change quickly and depend on harness details.
- Vendor-reported product benchmark numbers, because methodology may vary.
- Economic projections, because adoption and workflow redesign are uncertain.

Low confidence:

- Exact 2027-2028 autonomy levels across enterprises.
- Which framework will dominate; ecosystem is still fluid.
