---
description: "~/.claude 동기화 시 skills/, commands/, settings.json은 포함하고, settings.local.json, history.jsonl, projects/는 제외해야 한다. projects/는 절대 경로로 추적되어 다른 기기에서 충돌을 일으킨다."
type: methodology
created: 2026-03-29
source_verification: "2차해석"
evidence_level: "interpretation"
applicability: "High"
topic: "tech"
tags:
  - claude-code
  - sync
  - dotfiles
  - configuration
source_url: "https://x.com/NickSpisak_/status/2037192071254048947"
source_author: "Nick Spisak"
---

다중 기기에서 Claude Code 환경을 동기화할 때 동기화 대상을 주의해야 한다:

**동기화 포함:**
- ~/.claude/skills — 커스텀 스킬
- ~/.claude/commands — 커스텀 명령어
- ~/.claude/settings.json — 전역 설정

**동기화 제외:**
- ~/.claude/settings.local.json — 기기별 로컬 설정
- ~/.claude/history.jsonl — 히스토리 (기기별 분리 권장)
- ~/.claude/projects/ — 프로젝트 경로가 절대 경로로 저장되어 다른 기기에서 오류 발생

특히 projects/ 폴더는 절대 경로로 추적되므로, 사용자명이 다른 기기에서는 Claude가 프로젝트를 찾지 못한다. 해결책: 두 기기에서 동일한 사용자명을 사용하거나 projects/를 동기화하지 않는다.

---
Source:: [[2026-03-27-claude-channels-mac-mini-24-7-setup]]
Topics:: [[Tech]]