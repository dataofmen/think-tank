---
description: "측정 가능하고 효율적으로 평가할 수 있는 메트릭이라면 에이전트 스웜을 통해 자동 최적화 가능하다는 원칙. 효율적 프록시 메트릭이 존재하는 영역에서 즉시 적용 가능하나, Goodhart's Law 리스크 존재."
type: claim
created: 2026-03-27
source_verification: "1차자료"
evidence_level: "interpretation"
applicability: "High"
topic: "ai-productivity"
tags:
  - ai-agent
  - autoresearch
  - metric-optimization
  - proxy-metrics
source_url: "https://x.com/karpathy/status/2031135152349524125"
source_author: "Andrej Karpathy"
---

Karpathy는 autoresearch의 적용 범위를 일반화한다: "reasonably efficient to evaluate"한 메트릭이라면 에이전트 스웜을 통한 자동 최적화가 가능하며, 효율적 프록시 메트릭(예: 더 작은 네트워크 학습)이 있다면 더욱 실용적이다. 핵심 질문은 "당신의 문제가 이 범주에 해당하는가"이다.

적용 범위의 제약도 명확하다. 평가 비용이 높은 메트릭(사용자 만족도, 장기 리텐션 등)은 빠른 반복 실험이 불가능하고, 프록시 메트릭과 실제 메트릭의 괴리(Goodhart's Law)가 발생할 수 있다. 그럼에도 효율적 프록시가 존재하는 영역에서는 즉시 적용 가능하며, 적용 범위를 점진적으로 확장하는 전략이 합리적이다.

---
Source:: [[2026-03-27-ai-productivity-autoresearch-agent-optimization]]
Topics:: [[AI Productivity]]
Related:: [[Autoresearch pattern requires a measurable metric, code access, and experiment history tracking]] — 측정 가능 메트릭 요건을 적용 범위 관점에서 확장
Related:: [[Recursive evaluation-improvement loops raised AI agent first-pass quality from 40 percent to 94 percent]] — 6개 pass/fail 기준이 efficiently evaluable metric의 구체적 적용 사례
Related:: [[FSRS algorithm trained on 700 million reviews optimizes spaced repetition beyond traditional schedulers]] — 커뮤니티 스케일 데이터가 전문가 휴리스틱을 초월하는 동일 패턴을 학습 스케줄링 영역에서 실증
Related:: [[EWMA with decay factor 0.94 is a widely adopted standard for short-term volatility estimation]] — 변동성 추정의 감쇠 계수가 autoresearch로 최적화 가능한 구체적 사례
