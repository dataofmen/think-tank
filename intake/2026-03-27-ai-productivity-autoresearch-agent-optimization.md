---
title: "AI 에이전트가 신경망 학습을 자율적으로 최적화하여 수십 년 경력의 전문가도 놓친 개선점을 발견했다"
source: "1차자료"
url: "https://x.com/karpathy/status/2031135152349524125"
date: 2026-03-27
topic: "ai-productivity"
applicability: "High"
author: "Andrej Karpathy"
published: 2026-03-10
tags:
  - ai-agent
  - autoresearch
  - neural-network-optimization
  - autonomous-agent
  - LLM
  - agent-swarm
type: "twitter"
---

## 주요 주장 분석

1. 🟢 **Autoresearch 에이전트가 nanochat의 validation loss를 개선하는 ~20개 변경을 자율적으로 발견했고, 모두 additive하며 더 큰 모델에도 전이됨**
   - 근거: 실제 GitHub 커밋으로 검증 가능, Time to GPT-2 2.02h→1.80h (~11% 개선) 정량 측정

2. 🟢 **에이전트가 ~700개 변경을 자율적으로 실험하며, 이전 실험 결과를 기반으로 다음 실험을 계획함**
   - 근거: Karpathy 본인의 1차 경험, 구체적 발견 사항 나열 (QKnorm scaler 누락, Value Embeddings 정규화 미적용, banded attention 보수적 설정, AdamW betas 오류 등)

3. 🟡 **모든 LLM 프론티어 랩이 이 방식을 채택할 것이며, 이것이 "final boss battle"이다**
   - 해석: 20년 경력 전문가의 전문적 예측. 원리적으로 타당하나 대규모 확장의 복잡성은 인정

4. 🟠 **에이전트 스웜이 협업하여 점진적으로 더 큰 스케일로 아이디어를 프로모션하는 방식이 작동할 것**
   - 추정: 아직 "looking at" 단계. 단일 에이전트 성공에서 멀티 에이전트 협업으로의 도약은 미검증

5. 🟡 **측정 가능한 모든 메트릭은 에이전트 스웜으로 autoresearch 가능하다**
   - 해석: "reasonably efficient to evaluate" 조건 부여. 범용적 원칙으로서 타당하나 도메인별 제약 존재

---

## 반대 시나리오

### 주장 1: 에이전트 자율 최적화가 전문가를 능가
- **틀릴 수 있는 조건**: nanochat은 단일 train.py 파일의 비교적 단순한 설정. 실제 프론티어 모델은 분산 학습, 데이터 파이프라인, 인프라 등 복잡성이 수십 배. 에이전트가 시스템 수준의 문제를 다룰 수 있는지는 별개 문제.
- **그럼에도 유효한 이유**: 20년 경력 전문가가 이미 충분히 튜닝한 프로젝트에서도 놓친 점을 발견. 에이전트의 exhaustive search 능력은 인간의 직관과 상호보완적.

### 주장 2: 모든 프론티어 랩이 채택할 것
- **틀릴 수 있는 조건**: 에이전트 비용(컴퓨팅, API 호출)이 개선폭 대비 비효율적일 수 있음. 보안/IP 관점에서 에이전트에 핵심 학습 코드 접근을 허용하기 어려울 수 있음.
- **그럼에도 유효한 이유**: 경쟁적 압력 하에서 11% 성능 개선은 무시할 수 없는 이점. "Just engineering" 문제라면 시간 문제.

### 주장 3: 범용 메트릭 최적화 가능
- **틀릴 수 있는 조건**: 평가 비용이 높은 메트릭(사용자 만족도, 장기 리텐션 등)은 빠른 반복 실험이 불가능. 프록시 메트릭과 실제 메트릭의 괴리(Goodhart's Law).
- **그럼에도 유효한 이유**: 효율적 프록시가 존재하는 영역에서는 즉시 적용 가능. 적용 범위를 점진적으로 확장하면 됨.

---

## 적용성 분석

**적용성 점수**: High

### 연결점
- 포트폴리오: [PRJ-005] AI 기반 설문 설계 에이전트 — 에이전트가 메트릭 기반으로 반복 최적화하는 패턴이 설문 품질 자동 개선에 적용 가능
- 포트폴리오: [PRJ-004] NPS 데이터 처리 자동화 — 자동화된 실험-평가 루프의 설계 원칙 참고
- 의사결정: AI 에이전트 활용 범위를 "코드 생성"에서 "자율 최적화"로 확장할지 여부
- 액션: autoresearch 패턴(메트릭 정의 → 에이전트에 코드 접근권 → 자율 실험 → 결과 스태킹)을 자체 워크플로우에 적용 검토

### 구체적 활용 방안
- autoresearch의 핵심 패턴을 추상화: "측정 가능한 메트릭 + 코드 수정 권한 + 실험 이력 기반 계획" → 설문 설계, 데이터 파이프라인 최적화 등에 적용
- 에이전트의 exhaustive search가 인간의 직관적 튜닝을 보완하는 모델로 자체 AI 워크플로우 재설계 검토

### work-manager 연동 제안
- 연동 필요: Yes
- 대상 카드: [PRJ-005] AI 기반 설문 설계 에이전트

---

## 원문 발췌 (중요 부분만)

> Seeing the agent do this entire workflow end-to-end and all by itself as it worked through approx. 700 changes autonomously is wild. It really looked at the sequence of results of experiments and used that to plan the next ones.

> It's not novel, ground-breaking "research" (yet), but all the adjustments are "real", I didn't find them manually previously, and they stack up and actually improved nanochat.

> And more generally, *any* metric you care about that is reasonably efficient to evaluate (or that has more efficient proxy metrics such as training a smaller network) can be autoresearched by an agent swarm. It's worth thinking about whether your problem falls into this bucket too.

> Neural architecture search as it existed then is such a weak version of this that it's in its own category of totally useless by comparison. This is an *actual* LLM writing arbitrary code, learning from previous experiments, with access to the internet. It's not even close.

---
Source:: [[2026-03-10-karpathy-autoresearch-nanochat-results]]
