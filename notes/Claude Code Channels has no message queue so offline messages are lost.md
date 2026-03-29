---
description: "Claude Code Channels는 메시지 큐가 없어서, Claude 세션이 꺼져 있을 때 보낸 메시지가 유실된다. 나중에 대기열에 들어가지 않고 그냥 사라진다. 24/7 운용을 위해서는 세션을 항상 살려두거나 별도 메시지 보관 메커니즘이 필요하다."
type: problem
created: 2026-03-29
source_verification: "2차해석"
evidence_level: "interpretation"
applicability: "High"
topic: "ai-productivity"
tags:
  - claude-code
  - channels
  - reliability
  - offline
source_url: "https://x.com/NickSpisak_/status/2037192071254048947"
source_author: "Nick Spisak"
---

Claude Code Channels의 중요한 제약사항: 메시지 큐가 없다. Claude 세션이 실행 중이지 않을 때(예: Mac Mini 재부팅, 크래시, 의도적 중지) 보낸 Telegram 메시지는 대기열에 들어가지 않고 유실된다.

이는 24/7 AI 어시스턴트 운용에 치명적일 수 있다. 해결책:
1. LaunchAgent로 세션을 항상 유지
2. 별도 메시지 보관 봇을 앞에 두어 오프라인 메시지를 저장
3. 다른 세션에서 Claude를 시작할 때 대기 메시지 확인

---
Source:: [[2026-03-27-claude-channels-mac-mini-24-7-setup]]
Topics:: [[AI Productivity]]