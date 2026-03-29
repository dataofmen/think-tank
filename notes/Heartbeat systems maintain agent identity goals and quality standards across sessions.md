---
description: "Heartbeat 시스템은 에이전트의 정체성, 목표, 품질 기준을 세션 간에 유지하는 메커니즘이다. LLM은 도메인 맥락과 조직 문화를 자동으로 학습하지 못하므로, 명시적인 heartbeat로 에이전트가 '누구인지, 무엇을 하는지, 어떻게 판단하는지'를 지속적으로 인지한다."
type: methodology
created: 2026-03-29
source_verification: "2차해석"
evidence_level: "interpretation"
applicability: "High"
topic: "ai-productivity"
tags:
  - heartbeat
  - agent-management
  - paperclip
  - context
  - quality
source_url: "https://x.com/startupideaspod/status/2037247132927926452"
source_author: "@startupideaspod"
---

Heartbeat 시스템은 에이전트 관리의 핵심이다. 에이전트가 세션 간에 일관성 있게 동작하려면 다음을 지속적으로 인지해야 한다:

1. **정체성(Identity)** — 이 에이전트는 누구인가? 어떤 역할을 맡았는가?
2. **목표(Goals)** — 무엇을 달성해야 하는가? 성공의 정의는?
3. **품질 기준(Quality Standards)** — 어떤 기준으로 결과를 판단하는가?

이는 "AI는 모든 것을 할 수 있지만, 당신의 가치관을 공유할 수는 없다"는 문제를 해결한다. 모델 자체의 정렬(alignment) 기술이 발전해도, 특정 조직의 맥락과 문화는 명시적으로 인코딩해야 한다. [[Separating evaluation systems from generation layers enables continuous autonomous quality improvement|evaluation/generation 분리가 자율 품질 개선의 전제조건]]인 것처럼, heartbeat도 에이전트 품질 유지를 위한 구조적 장치다. [[Autoresearch pattern requires a measurable metric, code access, and experiment history tracking|autoresearch 패턴이 메트릭/코드접근/실험이력을 요구]]하는 것처럼, heartbeat도 에이전트가 자신의 정체성과 목표를 지속적으로 확인하는 메커니즘이다.

---
Source:: [[2026-03-27-ai-agent-orchestration-paperclip]]
Topics:: [[AI Productivity]]