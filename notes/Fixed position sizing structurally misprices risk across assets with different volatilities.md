---
description: "Allocating equal dollar amounts to contracts with 40% vs 5% volatility creates 8x difference in actual risk exposure, making fixed sizing a systematic error in portfolio construction."
type: claim
created: 2026-03-29
source_verification: "2차해석"
evidence_level: "fact"
applicability: "Low"
topic: "data-analysis"
tags:
  - position-sizing
  - risk-management
  - volatility
  - portfolio-construction
source_url: "https://x.com/noisyb0y1/status/2037797881701142678"
source_author: "@noisyb0y1 (Noisy)"
---

Fixed position sizing treats all assets as equally risky, which is mathematically incorrect. When two contracts have vastly different volatilities — say 40% versus 5% — investing the same dollar amount means the high-volatility contract dominates portfolio risk by a factor of 8x. This is not a subtle edge case but a structural flaw in how most retail traders size positions. The original author frames it directly: "Position sizing kills accounts more often than any bad trade." Risk-aware sizing must account for the realized volatility of each individual asset to maintain consistent risk exposure across the portfolio. [[Volatility targeting normalizes risk exposure through the ratio of target to realized volatility]] provides the mathematical solution to this structural flaw.

---
Source:: [[2026-03-29-volatility-targeting-polymarket-position-sizing]]
Derived:: [[2026-03-29-data-analysis-volatility-targeting-position-sizing]]
Topics:: [[Data Analysis]]
Related:: [[Correlated contracts on the same event represent one position regardless of nominal diversification]] — 연관 계약을 분산으로 착각하면 이 구조적 결함이 악화됨
