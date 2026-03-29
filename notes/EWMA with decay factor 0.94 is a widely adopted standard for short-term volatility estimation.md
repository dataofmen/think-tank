---
description: "RiskMetrics proposed the 0.94 decay factor for daily EWMA volatility, and it became an industry default, though individual funds tune this parameter to their specific needs."
type: claim
created: 2026-03-29
source_verification: "2차해석"
evidence_level: "interpretation"
applicability: "Low"
topic: "data-analysis"
tags:
  - EWMA
  - volatility-estimation
  - RiskMetrics
  - quantitative-finance
source_url: "https://x.com/noisyb0y1/status/2037797881701142678"
source_author: "@noisyb0y1 (Noisy)"
---

Exponentially Weighted Moving Average (EWMA) with a decay factor of 0.94 weights recent observations more heavily when estimating volatility. This specific parameter was proposed by JP Morgan's RiskMetrics framework and became a de facto standard across the industry for daily volatility estimation. The 0.94 value implies roughly a 17-day effective window, balancing responsiveness to new data against noise from short-term fluctuations. However, calling it a universal "standard" overstates the case — different funds and risk systems adjust this parameter based on their specific asset class, rebalancing frequency, and risk appetite. The value remains a reasonable default for practitioners who lack a systematic way to optimize the decay factor for their context. Its output feeds directly into [[Volatility targeting normalizes risk exposure through the ratio of target to realized volatility|volatility targeting formulas]]. Notably, since forecast accuracy against realized volatility is efficiently evaluable, the decay parameter is a candidate for systematic optimization — [[Any efficiently evaluable metric can be autoresearched by an agent swarm]].

---
Source:: [[2026-03-29-data-analysis-volatility-targeting-position-sizing]]
Topics:: [[Data Analysis]]
Related:: [[Any efficiently evaluable metric can be autoresearched by an agent swarm]] — applies autoresearch to volatility parameter tuning
