---
description: "macOS LaunchAgent는 사용자 세션 내에서 실행되어 인증 정보에 접근할 수 있으므로, cron 대신 사용하면 Claude Code가 사용자의 로그인 credential을 사용할 수 있다. 매일 특정 시간에 자동 재시작이 가능하다."
type: methodology
created: 2026-03-29
source_verification: "2차해석"
evidence_level: "interpretation"
applicability: "High"
topic: "tech"
tags:
  - launchagent
  - macos
  - automation
  - cron
  - infrastructure
source_url: "https://x.com/NickSpisak_/status/2037192071254048947"
source_author: "Nick Spisak"
---

macOS에서 Claude Code를 자동 재시작할 때 cron 대신 LaunchAgent를 사용해야 한다. cron은 stripped-down 환경에서 실행되어 사용자의 로그인 credential에 접근할 수 없지만, LaunchAgent는 사용자 세션 내에서 실행되므로 인증 정보를 사용할 수 있다.

LaunchAgent plist와 restart 스크립트를 조합하면 tmux 세션에서 Claude Code를 매일 특정 시간(예: 새벽 4시)에 자동 재시작할 수 있다. 이는 24/7 운용을 위한 핵심 패턴이다. [[A Mac Mini and Telegram bot can run a personal AI agent system 24-7 for months without reliability issues|소비자 하드웨어 기반 24/7 에이전트 운영]]에서 macOS launchd 스케줄러가 핵심 인프라 요소였는데, LaunchAgent가 그 구체적 구현 방식을 제공한다.

---
Source:: [[2026-03-27-claude-channels-mac-mini-24-7-setup]]
Topics:: [[Tech]]