---
description: "Sparkwave's production system applies 6 pass/fail criteria to every output, diagnoses failures, and patches the generation layer — achieving 94% first-pass rate from an initial 40%."
type: claim
created: 2026-03-27
source_verification: "1차자료"
evidence_level: "fact"
applicability: "High"
topic: "ai-productivity"
tags:
  - ai-agent
  - self-improvement
  - evaluation-loop
  - quality-assurance
source_url: "https://medium.com/@ScottSparkwave/building-self-improvement-into-ai-agents-4b345e3b27e6"
source_author: "Scott Johnson (Sparkwave AI)"
---

Sparkwave built an evaluation system that sits between AI output and the customer, running every response through 6 task-specific pass/fail criteria: Relevance, Question Answered, Detail Echo, Context Aware, Accuracy, and CTA Appropriate. When a response fails, the system diagnoses the specific failure mode, applies a targeted revision, and re-evaluates. This catch-diagnose-improve cycle brought first-pass quality from 40% to 94%.

The pattern mirrors autoresearch: a measurable metric (pass rate), code-level access (generation layer prompts), and experiment history (failure pattern logs) form the loop — the same three elements identified in [[Autoresearch pattern requires a measurable metric, code access, and experiment history tracking]]. The key constraint is that the task must have efficiently evaluable criteria — confirming that [[Any efficiently evaluable metric can be autoresearched by an agent swarm]]. Structured outputs like lead responses are ideal, while creative or ambiguous tasks may resist clean pass/fail decomposition. The architectural prerequisite for this loop is [[Separating evaluation systems from generation layers enables continuous autonomous quality improvement|separating evaluation from generation]].

---
Source:: [[2026-03-27-ai-productivity-ai-agent-self-improvement-loop]]
Topics:: [[AI Productivity]]
