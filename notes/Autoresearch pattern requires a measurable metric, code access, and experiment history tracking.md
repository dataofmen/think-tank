---
description: "Autoresearch의 핵심 패턴을 3요소로 추상화: (1) 측정 가능한 메트릭 정의, (2) 에이전트에 코드 수정 권한 부여, (3) 실험 이력 기반 계획. 이 패턴은 ML 학습 외에도 설문 설계, 데이터 파이프라인 등에 적용 가능."
type: methodology
created: 2026-03-27
source_verification: "2차해석"
evidence_level: "interpretation"
applicability: "High"
topic: "ai-productivity"
tags:
  - ai-agent
  - autoresearch
  - methodology
  - workflow-design
source_url: "https://x.com/karpathy/status/2031135152349524125"
source_author: "Andrej Karpathy"
---

Karpathy의 autoresearch 사례에서 추출한 핵심 패턴은 세 가지 요소로 구성된다: (1) 측정 가능한 메트릭을 명확히 정의하고, (2) 에이전트에 코드 수정 권한을 부여하며, (3) 실험 이력을 기반으로 다음 실험을 계획하게 한다. 결과는 스태킹(누적)되어야 한다.

이 패턴은 ML 학습 최적화를 넘어 범용적으로 적용 가능하다. 설문 설계 에이전트가 응답 완료율을 메트릭으로 설문 구조를 반복 최적화하거나, 데이터 파이프라인에서 처리 시간을 메트릭으로 코드를 자율 개선하는 시나리오에 동일 패턴이 적용된다. 핵심은 에이전트의 exhaustive search가 인간의 직관적 튜닝을 보완하는 상호보완 모델이라는 점이다.

---
Source:: [[2026-03-27-ai-productivity-autoresearch-agent-optimization]]
Topics:: [[AI Productivity]]
