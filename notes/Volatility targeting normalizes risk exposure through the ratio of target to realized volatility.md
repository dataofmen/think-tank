---
description: "The core formula leverage = target_vol / realized_vol is a standard quantitative finance technique validated by Moskowitz, Ooi, Pedersen (2012) and widely used in professional fund management."
type: methodology
created: 2026-03-29
source_verification: "2차해석"
evidence_level: "fact"
applicability: "Low"
topic: "data-analysis"
tags:
  - volatility-targeting
  - position-sizing
  - quantitative-finance
  - risk-management
source_url: "https://x.com/noisyb0y1/status/2037797881701142678"
source_author: "@noisyb0y1 (Noisy)"
---

Volatility targeting uses a single formula — leverage equals target volatility divided by realized volatility — to dynamically adjust position sizes so that every asset contributes the same amount of risk in dollar terms. When an asset's realized volatility is high, exposure shrinks; when it is low, exposure grows. The technique is well-established in academic literature (Moskowitz, Ooi, Pedersen 2012) and practiced across professional quant funds. The key insight: "You can never control your returns but risk you can." Practical implementation requires guardrails such as a leverage cap (e.g. 2x) and minimum allocation floor (e.g. 20%) to prevent extreme positions during volatility regime changes.

---
Source:: [[2026-03-29-data-analysis-volatility-targeting-position-sizing]]
Topics:: [[Data Analysis]]
