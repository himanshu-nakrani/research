# 04 — Enterprise Adoption and Economics

Last updated: 2026-05-22 IST

## 1. The enterprise opportunity

Agentic AI aims at the gap between software and services. Traditional software helps humans do work. Agents can potentially perform parts of the work: gather information, decide next steps, execute workflows, and escalate exceptions.

OWASP's 2025 agentic AI security/governance report frames the economic potential as expanding beyond the software market into the much larger services economy, because agents can act across tools and workflows rather than merely provide software features.

McKinsey and Accenture both argue that the value comes from reimagining processes, not just plugging agents into existing tasks.

## 2. Current adoption: broad experimentation, narrow scaling

McKinsey 2025:

- 88% of surveyed organizations use AI in at least one business function.
- 62% are at least experimenting with agents.
- 23% are scaling agentic AI somewhere.
- Most scaling is limited to one or two functions.

Deloitte 2026:

- 30% exploring.
- 38% piloting.
- 14% ready to deploy.
- 11% using in production.
- 35% have no formal strategy.

This indicates a classic transition from pilots to industrialization.

## 3. Where enterprises are using agents first

High-probability early use cases:

| Function | Agentic use cases | Why it fits |
|---|---|---|
| IT | Service desk triage, incident summaries, runbook execution, access requests | Tools and policies already exist; outcomes are trackable. |
| Software engineering | Bug fixes, tests, documentation, code review, migration | Fast verification through tests and diffs. |
| Knowledge management | Deep research, document synthesis, policy Q&A | High information load, low direct side effects. |
| Customer support | Case resolution, refund workflows, account changes with approval | Structured policies and tools; high volume. |
| Finance/G&A | Invoice processing, reconciliation, reporting | Repetitive workflows; needs strong controls. |
| Sales/marketing | Account research, campaign briefs, CRM updates | Many low-risk drafts plus some controlled writes. |
| HR | Employee Q&A, onboarding, ticket triage | Policy-heavy; privacy-sensitive. |

## 4. Why pilots fail

Deloitte identifies three infrastructure obstacles:

1. Legacy system integration: old systems lack real-time APIs, modular architecture, and secure identity for agentic execution.
2. Data architecture constraints: data is not searchable, reusable, contextualized, or agent-ready.
3. Governance/control frameworks: traditional IT governance does not fit autonomous systems making decisions and taking actions.

McKinsey similarly argues that organizations must move from scattered pilots to strategic programs, from use cases to business processes, from siloed AI teams to cross-functional transformation squads, and from experimentation to industrialized delivery.

## 5. Workflow redesign beats task automation

A weak approach:

> Take an existing human process and ask an agent to click through it faster.

A stronger approach:

> Redesign the process so agents receive structured context, call purpose-built tools, verify intermediate state, escalate exceptions, and produce auditable artifacts.

Example: invoice processing

Weak version:

- Agent opens email, downloads invoice, manually enters fields into ERP UI.

Agent-native version:

- Ingestion service extracts invoice.
- Agent checks vendor, contract, PO, anomalies.
- Tool creates a staged payment request.
- Policy engine determines approval requirement.
- Human approves exceptions.
- Audit log records evidence and decision path.

## 6. The emerging "agentic organization"

McKinsey describes a shift toward an "agentic organization" where humans, virtual agents, and physical agents work together. It argues operating models will move toward flatter, outcome-aligned, AI-first teams.

Key organizational changes:

- Humans shift from execution to supervision, orchestration, exception handling, and design.
- Teams manage portfolios of agents, not just software tools.
- Governance becomes continuous and runtime-based.
- Roles emerge around agent operations, evaluation, context engineering, and AI risk.
- Value measurement moves from seat adoption to workflow-level outcomes.

## 7. Economics and ROI

Agent economics depend on:

- Task value.
- Success rate.
- Cost per run.
- Human review time.
- Error cost.
- Latency tolerance.
- Integration cost.
- Monitoring and governance cost.

A simple ROI formula:

```text
Expected value per run =
  (probability_success * value_of_success)
  - (probability_error * cost_of_error)
  - model/tool/runtime_cost
  - human_review_cost
  - amortized_integration_and_governance_cost
```

Agents are most attractive when:

- Volume is high.
- Human time is expensive.
- Errors are recoverable.
- Verification is strong.
- Tools are already available.
- Context is structured.
- The task has measurable outcomes.

## 8. Build vs buy

Buy when:

- The workflow is common and vendor-supported.
- You need enterprise compliance quickly.
- Integration with existing SaaS is the main value.
- Differentiation is low.

Build when:

- Workflow is core to competitive advantage.
- You need custom permissions or domain logic.
- Data/context layer is unique.
- Vendor black boxes create unacceptable risk.
- You need deep integration with internal systems.

Hybrid is common: buy platform primitives, build domain-specific tools, policies, and evaluation suites.

## 9. Enterprise readiness checklist

Before scaling agents, an organization needs:

- Clear owner for agentic AI strategy.
- Inventory of workflows by value/risk.
- Agent-ready identity and access management.
- Data catalog and retrieval layer.
- Tool/API inventory with least-privilege scopes.
- Sandbox and staging environments.
- Human approval policies.
- Evaluation harnesses and red-team tests.
- Observability and trace replay.
- Incident response plan for agent failures.
- Legal/compliance review for autonomy and data use.

## 10. Strategic conclusion

The winners will not be the organizations with the most demos. They will be the organizations that redesign work around reliable, governed, measurable human-agent systems.

Agentic AI is less like installing a chatbot and more like onboarding a new class of digital worker: it needs job descriptions, permissions, training data, supervision, metrics, audits, and offboarding.
