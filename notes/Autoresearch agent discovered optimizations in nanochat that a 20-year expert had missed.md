---
description: "Karpathy의 nanochat 프로젝트에서 AI 에이전트가 ~700개 변경을 자율 실험하여 ~20개 유효한 개선을 발견, GPT-2 학습 시간을 11% 단축(2.02h→1.80h). 모든 개선이 additive하며 더 큰 모델에도 전이됨."
type: claim
created: 2026-03-27
source_verification: "1차자료"
evidence_level: "fact"
applicability: "High"
topic: "ai-productivity"
tags:
  - ai-agent
  - autoresearch
  - neural-network-optimization
  - autonomous-agent
source_url: "https://x.com/karpathy/status/2031135152349524125"
source_author: "Andrej Karpathy"
---

Karpathy가 이미 충분히 튜닝한 nanochat(단일 train.py 기반 LLM 학습 프로젝트)에서 AI 에이전트가 자율적으로 ~700개 변경을 실험하여 ~20개의 유효한 최적화를 발견했다. QKnorm scaler 누락, Value Embeddings 정규화 미적용, banded attention의 보수적 설정, AdamW betas 오류 등 구체적인 발견이 포함된다.

핵심은 이 발견들이 "novel research"가 아닌 실질적인 엔지니어링 개선이면서도, 20년 경력의 전문가가 놓친 것들이라는 점이다. 에이전트의 exhaustive search 능력이 인간의 직관적 튜닝과 상호보완적임을 실증한다. 단, nanochat은 비교적 단순한 설정이므로 분산 학습 등 복잡한 시스템으로의 확장성은 별개 문제다.

---
Source:: [[2026-03-27-ai-productivity-autoresearch-agent-optimization]]
Topics:: [[AI Productivity]]
