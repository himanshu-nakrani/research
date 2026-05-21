# 01 — Current State of Agentic AI

Last updated: 2026-05-22 IST

## 1. What "agentic AI" means

A practical definition:

> Agentic AI is an AI system that can pursue a goal through multiple steps by observing state, reasoning or planning, using tools, taking actions, and adapting based on feedback.

This separates agents from ordinary chatbots. A chatbot mostly returns text. An agent changes state: it edits files, books things, calls APIs, drives a browser, updates a CRM, runs tests, sends messages, or coordinates other agents.

Core properties:

- Goal-directed: works toward an outcome, not only a response.
- Tool-using: calls APIs, searches, writes files, runs code, controls browsers or computers.
- Feedback-driven: observes results, catches errors, retries or changes plan.
- Contextual: uses memory, retrieved documents, logs, prior actions, and task state.
- Bounded autonomy: may operate independently within configured permissions, then escalate.

## 2. Why agents accelerated in 2025

Several streams matured at the same time:

1. Reasoning models improved planning, decomposition, and self-correction.
2. Tool-use training became mainstream in frontier models.
3. Coding agents demonstrated that LLMs can complete real work when given a shell, editor, tests, and version control.
4. Browser/computer-use models learned to operate interfaces directly, not only APIs.
5. Frameworks and SDKs began standardizing loops, handoffs, guardrails, sessions, tracing, and sandboxing.
6. Enterprise buyers began moving from experimentation to workflow transformation.

OpenAI's Computer-Using Agent (CUA), introduced in January 2025, represents the browser/computer-control direction: it processes screenshots, reasons, and acts with a virtual mouse and keyboard. OpenAI reported 38.1% success on OSWorld, 58.1% on WebArena, and 87% on WebVoyager, while noting the gap to human performance on harder tasks.

OpenAI later introduced ChatGPT agent in July 2025, combining Operator-style web interaction, deep research synthesis, a terminal, browser tools, APIs, and connectors into one virtual-computer workflow.

Anthropic's Claude Code and Claude Agent SDK represent the "give the model a computer" direction: file access, bash, search, edit, verify, repeat. Anthropic describes a common loop: gather context -> take action -> verify work -> repeat.

Google's Gemini direction emphasizes a universal AI assistant and world-model framing: multimodal understanding, memory, computer control, Project Astra, and Project Mariner, including multiple browser agents working on tasks in parallel.

## 3. Adoption snapshot

Enterprise AI adoption is broad, but scaling agents is still early.

McKinsey's 2025 global survey reported:

- 88% of respondents say their organizations regularly use AI in at least one business function.
- 62% say their organizations are at least experimenting with AI agents.
- 23% say their organizations are scaling an agentic AI system somewhere in the enterprise.
- In any given business function, no more than 10% report scaling AI agents.
- Agent use is most commonly reported in IT and knowledge management.

Deloitte's 2026 Tech Trends article reports a similar production gap:

- 30% of surveyed organizations are exploring agentic options.
- 38% are piloting.
- 14% have solutions ready to deploy.
- 11% are actively using agentic systems in production.
- 42% are still developing an agentic roadmap and 35% have no formal strategy.

This suggests the industry has moved beyond pure curiosity, but not yet into broad operational maturity.

## 4. Product landscape

Major product categories:

| Category | Examples | Current maturity | Why it matters |
|---|---|---:|---|
| Coding agents | Claude Code, Codex-style agents, Cursor, Devin-like systems, OpenHands, SWE-agent | High relative maturity | Fast feedback loops make autonomy useful and measurable. |
| Research agents | ChatGPT deep research/agent, Claude Research, Perplexity-style systems | Medium-high | Parallel search and synthesis benefit from multi-agent breadth. |
| Browser/computer agents | Operator/CUA, Project Mariner, browser agents | Medium | Useful for long-tail tasks without APIs, but reliability and safety are hard. |
| Enterprise workflow agents | Salesforce, ServiceNow, Microsoft 365 Copilot agents, n8n/Zapier-style builders | Early-medium | Biggest economic prize, but integration/governance heavy. |
| Customer support agents | Tool/API agents with policy manuals | Medium | Clear workflows and escalation paths; high risk if permissions are broad. |
| Physical/robotic agents | Gemini Robotics, drones, humanoid prototypes | Early | Extends agentic AI into physical world; safety burden is much higher. |

## 5. What is actually working

The most reliable agent deployments tend to have:

- A narrow, valuable workflow.
- Clear success criteria.
- Tool APIs with typed schemas.
- Strong retrieval/context layer.
- Sandboxed execution.
- Automated verification.
- Human approval for irreversible or high-impact actions.
- Tracing and replay for debugging.
- Incremental autonomy levels.

Best-fit current tasks:

- Codebase Q&A, bug fixing, test generation, documentation, refactoring.
- Deep research with citations and synthesis.
- Data analysis with notebooks or scripts.
- Internal support workflows with structured tools and policies.
- Document processing where human review remains in the loop.
- Sales/marketing operations where actions can be staged before execution.

Weak-fit current tasks:

- High-stakes autonomous decisions without review.
- Tasks with ambiguous success criteria.
- Workflows requiring broad access to sensitive data plus external communications.
- Long-horizon tasks with many hidden dependencies.
- Browser tasks involving captchas, anti-bot systems, brittle UIs, or dynamic permissions.

## 6. The main bottleneck has shifted

The bottleneck is no longer only model intelligence. It is increasingly system design:

- Can the agent get the right context?
- Can it use tools safely?
- Can it verify work before side effects?
- Can humans understand and supervise it?
- Can the organization monitor and govern it?
- Can the workflow be redesigned instead of merely automated?

This is why agentic AI is better understood as a new software architecture and operating model, not simply a new model feature.
