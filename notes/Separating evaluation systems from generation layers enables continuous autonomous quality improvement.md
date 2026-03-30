---
description: "When evaluation logic is architecturally separate from generation logic, failure diagnosis can feed back into prompt/context updates without human intervention — creating a closed improvement loop."
type: methodology
created: 2026-03-27
source_verification: "1차자료"
evidence_level: "fact"
applicability: "High"
topic: "ai-productivity"
tags:
  - ai-agent
  - architecture
  - evaluation-loop
  - self-improvement
source_url: "https://medium.com/@ScottSparkwave/building-self-improvement-into-ai-agents-4b345e3b27e6"
source_author: "Scott Johnson (Sparkwave AI)"
---

Sparkwave's architecture cleanly separates two concerns: the generation layer (system prompts, context, instructions that shape output) and the evaluation layer (pass/fail gates that judge output quality). When a customer said "I work until 6" and the AI recommended a 6 PM class, the evaluation layer caught the error. Agent Rico then performed root cause analysis and patched the generation layer's time-constraint interpretation logic. Subsequent similar inputs passed on first attempt.

This separation is what makes the improvement loop autonomous — the evaluation layer acts as both quality gate and diagnostic signal, while the generation layer remains the single target for remediation. This structurally ensures two of the three elements in [[Autoresearch pattern requires a measurable metric, code access, and experiment history tracking]]: the evaluation layer provides the measurable metric, and the isolated generation layer provides clean code access. Without separation, failure signals and generation logic become entangled, making systematic improvement difficult. The quantitative payoff of this architecture is documented in [[Recursive evaluation-improvement loops raised AI agent first-pass quality from 40 percent to 94 percent|the 40%→94% improvement case]]. [[Heartbeat systems maintain agent identity goals and quality standards across sessions|Heartbeat 시스템]]도 에이전트 품질 유지를 위한 구조적 장치로, evaluation/generation 분리와 같은 맥락에서 이해할 수 있다.

---
Source:: [[2026-03-27-building-self-improvement-into-ai-agents]]
Derived:: [[2026-03-27-ai-productivity-ai-agent-self-improvement-loop]]
Topics:: [[AI Productivity]]
Related:: [[Multi-AI tool chaining outperforms single tools by assigning specialized strengths to each pipeline stage]] — 기능 분리 원칙이 에이전트 내부 아키텍처를 넘어 도구 간 파이프라인 수준에서도 동일하게 적용됨
