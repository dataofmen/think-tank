---
description: "기존 Neural Architecture Search와 달리, LLM 기반 autoresearch 에이전트는 이전 실험 결과를 분석하고 다음 실험을 계획하는 적응적 탐색을 수행한다. 임의 코드 작성과 인터넷 접근이 가능해 NAS와는 질적으로 다른 범주."
type: claim
created: 2026-03-27
source_verification: "1차자료"
evidence_level: "fact"
applicability: "High"
topic: "ai-productivity"
tags:
  - ai-agent
  - autoresearch
  - experiment-design
  - LLM
source_url: "https://x.com/karpathy/status/2031135152349524125"
source_author: "Andrej Karpathy"
---

Karpathy가 관찰한 autoresearch 에이전트의 핵심 차별점은 실험 결과의 시퀀스를 분석하여 다음 실험을 계획하는 적응적(adaptive) 탐색 능력이다. 에이전트는 약 700개의 변경을 자율적으로 실험하면서, 각 실험의 결과를 기반으로 탐색 방향을 조정했다.

이는 기존 Neural Architecture Search(NAS)와 근본적으로 다르다. Karpathy는 NAS를 "totally useless by comparison"이라 평가하며, 현재 에이전트는 임의의 코드를 작성하고, 이전 실험에서 학습하며, 인터넷에 접근할 수 있는 실제 LLM이라는 점을 강조한다. 탐색 공간이 사전 정의된 하이퍼파라미터가 아닌 코드 수준의 자유도를 가진다.

---
Source:: [[2026-03-27-ai-productivity-autoresearch-agent-optimization]]
Topics:: [[AI Productivity]]
Related:: [[Autoresearch agent discovered optimizations in nanochat that a 20-year expert had missed]] — 적응적 탐색 메커니즘이 어떻게 ~20개 유효 최적화 발견으로 이어졌는지 설명
Related:: [[AI agents that use their own capabilities to build new capabilities produce compound improvement effects]] — 적응적 실험 계획이 compound improvement를 생성하는 핵심 메커니즘
