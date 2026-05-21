# 03 — Benchmarks and Capabilities

Last updated: 2026-05-22 IST

## 1. Why agent benchmarks are hard

Agent benchmarks differ from classic ML benchmarks because success is end-to-end. An agent may browse, code, call tools, ask questions, update state, and produce artifacts. Evaluation must decide whether the real-world task was actually completed.

This creates problems:

- Success can be ambiguous.
- Tests may miss edge cases.
- String matching can reward wrong behavior.
- LLM judges can be inconsistent.
- Agents can exploit benchmark flaws.
- Fixed tasks can become contaminated.
- Scaffold, tools, time budget, retries, and permissions strongly affect scores.

A 2025 paper, "Establishing Best Practices for Building Rigorous Agentic Benchmarks," argues that many agent benchmarks have task or reward-design flaws. It reports that issues can over- or underestimate performance by up to 100% in relative terms, and gives examples such as tau-bench counting empty responses as successful and SWE-bench-Verified using insufficient tests in some cases.

## 2. Coding agents: the most mature frontier

SWE-bench is the canonical benchmark for software engineering agents. It asks systems to fix real GitHub issues in real repositories and pass tests.

The original SWE-bench paper reported that Claude 2 solved only 1.96% of tasks in its baseline setup, showing how hard real repository repair was in 2023-2024.

By 2025-2026, scores on SWE-bench Verified rose dramatically. Official and third-party trackers vary by harness and methodology, but the broad trend is clear: coding agents moved from near-zero success to majority success on the verified subset.

Important lessons:

- Base model matters, but scaffold matters too.
- Tools, search strategy, patch generation, test selection, retry policy, and review loops can move scores by double-digit percentage points.
- Easy subsets can saturate while frontier subsets remain hard.
- Real engineering still requires understanding requirements, avoiding regressions, and integrating with human workflows.

Why coding agents work earlier than general agents:

- Code has executable feedback.
- Tests/linters/compilers provide verification.
- Git creates reversible diffs.
- Repositories are structured information spaces.
- Developers can review patches before merge.

## 3. Browser and web agents

### WebArena

WebArena evaluates agents on realistic self-hosted websites across domains like e-commerce, forums, collaborative software development, and content management. The original ICLR 2024 paper reported a best GPT-4-based agent success rate of 14.41% versus 78.24% for humans.

OpenAI later reported CUA at 58.1% on WebArena, indicating major progress, but still below human reliability.

### WebVoyager

WebVoyager uses live websites. OpenAI reported CUA at 87% on WebVoyager, but notes that WebVoyager tasks are generally simpler than complex benchmarks like WebArena.

### WorkArena

WorkArena focuses on enterprise software tasks in ServiceNow. It contains 33 tasks and 19,912 unique instances. The paper emphasizes that enterprise UIs are a major potential area for agents but still show a gap toward full automation.

The extracted paper notes GPT-4o achieved 43% success on WorkArena versus much lower scores for GPT-3.5 and Llama3, highlighting strong dependence on frontier models.

### AssistantBench

AssistantBench asks whether web agents can solve realistic, time-consuming web tasks. The EMNLP 2024 paper reported that no model reached more than 25 points, and state-of-the-art web agents scored near zero in some settings. It found open-web navigation remains a major challenge.

## 4. Tool-use and conversational agents

### tau-bench

tau-bench evaluates tool-agent-user interaction in realistic domains such as airline and retail. It uses simulated users, domain tools, and policy guidelines.

The tau-bench repository reports, for example:

- Airline: Claude 3.5 Sonnet tool-calling pass^1 0.460; GPT-4o 0.420.
- Retail: Claude 3.5 Sonnet tool-calling pass^1 0.692; GPT-4o 0.604.

However, the repository warns that the old tasks are outdated and points to tau2/tau3-bench for fixed tasks and new domains. Benchmark-validity research also found flaws in older tau-bench evaluation design. Treat these numbers as historically useful but not definitive.

## 5. Full computer-use agents

### OSWorld

OSWorld evaluates agents controlling full operating systems. OpenAI reported CUA at 38.1% success, compared with human performance of 72.4%. This is a strong signal that computer-use agents are real, but still far from robust human-level autonomy.

Computer-use benchmarks are especially difficult because agents must:

- Interpret pixels and UI state.
- Use mouse/keyboard accurately.
- Recover from unexpected dialogs.
- Maintain task state over many steps.
- Avoid destructive side effects.

## 6. Research agents

Research agents are harder to benchmark because quality depends on coverage, source reliability, synthesis, and citation accuracy.

Anthropic reports that multi-agent research systems outperform single-agent systems on internal breadth-first research tasks, largely because subagents can explore independent branches in parallel and compress findings for a lead agent.

The key capability is not just search; it is iterative question refinement:

1. Decompose research topic.
2. Search independently.
3. Follow leads.
4. Compress findings.
5. Cross-check claims.
6. Add citations.
7. Synthesize an answer.

## 7. Benchmark interpretation checklist

When reading any agent benchmark, ask:

1. What tools were allowed?
2. Was the agent using a browser, API, shell, editor, or custom scaffold?
3. How much time and how many retries were allowed?
4. Was the model evaluated alone or inside a product system?
5. How was success measured?
6. Could tests be gamed?
7. Were tasks contaminated by training data or public leaderboards?
8. Was human performance measured under comparable conditions?
9. Are safety failures counted or only task success?
10. Are costs and latency reported?

## 8. Bottom line on capabilities

Current agents are impressive but uneven:

- Strongest: coding, structured research, data analysis, document workflows with review.
- Improving fast: browser tasks, enterprise UI tasks, multi-agent research, tool-use conversations.
- Still weak: open-ended long-horizon autonomy, high-stakes unsupervised action, robust security under adversarial input, physical-world autonomy.

The next evaluation frontier is not just "can it solve the task?" but:

- Can it solve the task reliably over repeated runs?
- Can it solve it safely under adversarial input?
- Can it explain and audit what happened?
- Can it do so at acceptable cost and latency?
