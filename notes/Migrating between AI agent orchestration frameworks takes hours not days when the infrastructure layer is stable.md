---
description: "OpenClaw에서 Hermes Agent로 3시간 내 마이그레이션 — 동일 하드웨어, 봇, LLM 유지하며 오케스트레이션만 교체. 14개 launchd + 25개 쉘스크립트를 통합 프레임워크로 단순화"
type: claim
created: 2026-03-29
source_verification: "1차자료"
evidence_level: "fact"
applicability: "High"
topic: "ai-productivity"
tags:
  - ai-agent
  - orchestration
  - migration
  - hermes-agent
  - architecture
source_url: "https://x.com/witcheer/status/2037528582298194123"
source_author: "witcheer"
---

witcheer는 AI 에이전트 오케스트레이션 프레임워크를 OpenClaw에서 Hermes Agent(Nous Research)로 약 3시간 만에 마이그레이션했다. 핵심은 인프라 레이어(Mac Mini M4, Telegram 봇, $21/월 GLM-5)를 그대로 유지하고 오케스트레이션 엔진만 교체한 것이다. 이 과정에서 14개 launchd 에이전트와 25개 쉘 스크립트가 통합 프레임워크로 단순화되었다. 이는 [[The bottleneck for AI agent capability was deployment infrastructure not model intelligence|배포 인프라가 에이전트 역량의 병목]]이라는 통찰을 레이어 분리 설계로 해소한 사례이며, [[Separating evaluation systems from generation layers enables continuous autonomous quality improvement|evaluation/generation 분리]]와 마찬가지로 AI 시스템에서 관심사 분리가 독립적 진화를 가능케 하는 반복 패턴임을 보여준다. [[Orchestration layers solve workflow chaos from running multiple AI agents simultaneously|오케스트레이션 레이어]]도 이 안정적 인프라의 구성 요소로, 프레임워크 교체가 수 시간 내에 가능하려면 오케스트레이션 레이어가 인프라와 명확히 분리되어 있어야 한다.

---
Source:: [[2026-03-27-ai-productivity-personal-ai-agent-setup]]
Topics:: [[AI Productivity]]
