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

witcheer는 AI 에이전트 오케스트레이션 프레임워크를 OpenClaw에서 Hermes Agent(Nous Research)로 약 3시간 만에 마이그레이션했다. 핵심은 인프라 레이어(Mac Mini M4, Telegram 봇, $21/월 GLM-5)를 그대로 유지하고 오케스트레이션 엔진만 교체한 것이다. 이 과정에서 14개 launchd 에이전트와 25개 쉘 스크립트가 통합 프레임워크로 단순화되었다. 이는 에이전트 시스템 설계 시 인프라 레이어와 오케스트레이션 레이어를 분리하면 프레임워크 락인 없이 빠르게 전환할 수 있음을 실증한다. 레이어 분리가 장기 유연성의 핵심이다.

---
Source:: [[2026-03-27-ai-productivity-personal-ai-agent-setup]]
Topics:: [[AI Productivity]]
