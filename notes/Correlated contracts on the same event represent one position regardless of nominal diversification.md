---
description: "Two prediction market contracts linked to the same political outcome are effectively one doubled position; separate volatility scaling gives a false sense of diversification."
type: claim
created: 2026-03-29
source_verification: "2차해석"
evidence_level: "fact"
applicability: "Low"
topic: "data-analysis"
tags:
  - correlation
  - diversification
  - position-sizing
  - prediction-markets
  - portfolio-risk
source_url: "https://x.com/noisyb0y1/status/2037797881701142678"
source_author: "@noisyb0y1 (Noisy)"
---

When multiple contracts are driven by the same underlying event, scaling them independently creates an illusion of diversification while concentrating actual risk. The original author states it plainly: "Two contracts on the same political outcome — that's not two positions. That's one position twice as large." In prediction markets like Polymarket, this is especially relevant because many contracts share the same resolution trigger (e.g., election outcomes, policy decisions). Portfolio-level volatility management must account for correlation structure, grouping correlated contracts and treating them as a single effective position for sizing purposes. While precise correlation data may be sparse in prediction markets, the heuristic of "same theme equals one position" provides a practical safeguard against hidden concentration risk.

---
Source:: [[2026-03-29-data-analysis-volatility-targeting-position-sizing]]
Topics:: [[Data Analysis]]
