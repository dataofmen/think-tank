---
title: "Polymarket 포지션 사이징을 위한 변동성 타겟팅 공식: leverage = target_vol / realized_vol"
source: "2차해석"
url: "https://x.com/noisyb0y1/status/2037797881701142678"
date: 2026-03-29
topic: "data-analysis"
applicability: "Low"
author: "@noisyb0y1 (Noisy)"
published: 2026-03-28
tags:
  - volatility-targeting
  - position-sizing
  - polymarket
  - risk-management
  - quantitative-trading
  - python
type: "twitter"
---

## 주요 주장 분석

1. 🟢 **변동성(Volatility)은 수익률의 표준편차로 측정하며, ATR과 거의 동치(SD ≈ ATR × 0.875)**
   - 근거: 금융공학 표준 정의. 교과서적 사실.

2. 🟢 **고정 포지션 사이즈는 자산별 위험을 동일시하므로 구조적으로 잘못됨**
   - 근거: 변동성 40%인 계약과 5%인 계약에 동일 금액 투입 시, 실질 리스크 노출이 8배 차이. 수학적으로 자명.

3. 🟢 **핵심 공식: leverage = target_vol / realized_vol**
   - 근거: 변동성 타겟팅(volatility targeting)은 학계와 퀀트 업계에서 널리 사용되는 표준 기법. Moskowitz, Ooi, Pedersen (2012) 등 다수 논문에서 검증.

4. 🟡 **EWMA decay factor 0.94가 전문 펀드의 표준**
   - 해석: RiskMetrics에서 제안한 값으로 널리 사용되나, "표준"이라고 단정하기엔 펀드마다 다양한 파라미터 사용.

5. 🟡 **변동성 타겟팅이 Sharpe ratio를 ~0.4에서 ~0.5로 개선**
   - 해석: 미국 주식 시장 백테스트 기반 주장. Moreira & Muir (2017) 등 연구가 있으나, 구체적 출처 미제시. 시장/기간에 따라 결과 상이.

6. 🟠 **변동성과 수익률 사이 음의 상관관계(leverage effect)가 항상 성립**
   - 추정: 주식시장에서는 잘 문서화된 현상이나, prediction market(Polymarket)에서 동일하게 적용된다는 근거 부족.

---

## 반대 시나리오

### 주장 1: 변동성 타겟팅이 리스크를 효과적으로 통제한다
- **틀릴 수 있는 조건**: 저변동성 환경에서 갑작스러운 regime change 발생 시 (예: 블랙스완 이벤트). 과거 변동성 기반이므로 급변에 후행 반응. 저자 본인도 Phase 9에서 이 한계를 인정.
- **그럼에도 유효한 이유**: 완벽한 예측은 불가능하나, leverage cap(2x)과 min_allocation(20%)으로 꼬리 위험을 구조적으로 제한. "없는 것보다 확실히 나은" 리스크 관리.

### 주장 2: Polymarket에 이 공식이 적용 가능하다
- **틀릴 수 있는 조건**: Polymarket 계약은 전통 금융자산과 달리 이진 결과(0 or 1), 제한된 유동성, 비연속적 가격 변동. 연속적 로그 수익률 가정이 맞지 않을 수 있음.
- **그럼에도 유효한 이유**: 만기 전까지 가격이 연속적으로 움직이는 기간이 존재하며, 다수 계약 포트폴리오에서 변동성 기반 포지션 조절의 직관은 여전히 유효.

### 주장 3: 상관관계를 고려한 포트폴리오 레벨 변동성 관리가 필수
- **틀릴 수 있는 조건**: Polymarket 계약 간 상관관계 데이터가 충분하지 않을 수 있으며, 상관관계 자체가 불안정.
- **그럼에도 유효한 이유**: 같은 정치 이벤트에 연동된 계약들의 상관관계는 직관적으로 파악 가능. 완벽한 공분산 행렬 없이도 "같은 테마 = 하나의 포지션"이라는 원칙은 실용적.

---

## 적용성 분석

**적용성 점수**: Low

### 연결점
- 포트폴리오: 현재 진행 중인 UX 리서치 프로젝트(PRJ-001~006)와 직접적 연관 없음
- 의사결정: 현재 고민 중인 결정과 무관
- 액션: 개인 투자/트레이딩에 관심이 있다면 적용 가능하나, 업무 맥락에서는 활용점 제한적

### 구체적 활용 방안
- Python 코드 포함 — 데이터 분석 방법론 레퍼런스로 보관 가능
- 변동성 타겟팅의 "리스크를 통제 가능한 것에 집중"이라는 원칙은 리서치 리소스 배분 의사결정에 메타포로 활용 가능

### work-manager 연동 제안
- 연동 필요: No

---

## 원문 발췌 (중요 부분만)

> Target vol / realized vol. That's the whole formula.

> You always aim for the same amount of risk in dollar terms. You can never control your returns but risk you can.

> Position sizing kills accounts more often than any bad trade.

> If your contracts are correlated - separate scaling will give a false sense of diversification. Two contracts on the same political outcome - that's not two positions. That's one position twice as large.

> Vol spikes -> you scale down -> market bounces -> you miss the recovery -> vol drops -> you scale up -> market falls again
