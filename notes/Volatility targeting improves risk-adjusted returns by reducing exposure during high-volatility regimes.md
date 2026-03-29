---
description: "Backtests on US equities suggest volatility targeting can lift Sharpe ratio from ~0.4 to ~0.5, supported by Moreira & Muir (2017), though results vary by market and time period."
type: claim
created: 2026-03-29
source_verification: "2차해석"
evidence_level: "interpretation"
applicability: "Low"
topic: "data-analysis"
tags:
  - volatility-targeting
  - Sharpe-ratio
  - risk-adjusted-returns
  - backtesting
source_url: "https://x.com/noisyb0y1/status/2037797881701142678"
source_author: "@noisyb0y1 (Noisy)"
---

Volatility targeting improves risk-adjusted returns primarily by scaling down positions during high-volatility periods, which tend to coincide with drawdowns. US equity market backtests show Sharpe ratio improvements from approximately 0.4 to 0.5. Research by Moreira & Muir (2017) provides academic support, though the magnitude of improvement is sensitive to market context and time period. The mechanism depends on the empirically observed negative correlation between volatility and returns (leverage effect). A known limitation is the whipsaw problem: volatility spikes trigger position reduction, the market recovers, and by the time volatility subsides and positions rebuild, the market may fall again. This lag is inherent to any backward-looking volatility measure.

---
Source:: [[2026-03-29-data-analysis-volatility-targeting-position-sizing]]
Topics:: [[Data Analysis]]
