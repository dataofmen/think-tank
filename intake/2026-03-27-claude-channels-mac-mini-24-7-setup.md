---
title: "Claude Code Channels + Mac Mini로 24/7 AI 어시스턴트 구축하기"
source: "2차해석"
url: "https://x.com/NickSpisak_/status/2037192071254048947"
date: 2026-03-27
topic: "ai-productivity"
applicability: "High"
author: "Nick Spisak (@NickSpisak_)"
published: 2026-03-26
tags:
  - claude-code
  - channels
  - telegram
  - mac-mini
  - syncthing
  - launchagent
  - automation
type: "twitter"
---

## 주요 주장 분석

1. 🟢 **Claude Code Channels는 Telegram/Discord/iMessage를 통해 원격으로 Claude와 대화할 수 있게 한다**
   - 근거: Anthropic 공식 기능. 실제 동작하는 셋업 가이드 제공

2. 🟢 **SyncThing으로 두 컴퓨터 간 무료 파일 동기화가 가능하다**
   - 근거: SyncThing은 2013년부터 운영 중인 오픈소스 프로젝트 (GitHub)

3. 🟡 **~/.claude/skills, commands, settings.json, knowledge base, MCP configs는 동기화해야 하고, settings.local.json, history.jsonl, projects/는 동기화하면 안 된다**
   - 해석: 실제 경험 기반 가이드. projects/ 폴더가 절대경로로 추적된다는 점은 Claude Code 동작 방식에 부합

4. 🟡 **Channels에는 메시지 큐가 없어서, 세션이 꺼져 있으면 메시지가 유실된다**
   - 해석: 저자의 실사용 경험 기반 주장. 공식 문서에서 확인 필요하나, 초기 기능으로서 합리적 제약

5. 🟢 **macOS LaunchAgent로 Claude Code를 자동 재시작할 수 있다**
   - 근거: LaunchAgent는 macOS 표준 기능. 제공된 plist/스크립트 코드가 기술적으로 정확

6. 🟡 **cron 대신 LaunchAgent를 써야 하는 이유: cron은 사용자 인증 정보에 접근 불가**
   - 해석: macOS 보안 모델상 맞는 설명. LaunchAgent는 user session 내에서 실행되어 credential 접근 가능

---

## 반대 시나리오

### 주장 1: Channels가 OpenClaw를 완전히 대체한다
- **틀릴 수 있는 조건**: OpenClaw가 메시지 큐, 멀티 에이전트 관리 등 Channels에 없는 고급 기능을 제공한다면 완전 대체는 아님. Channels가 아직 초기 기능이라 안정성이 검증되지 않았을 수 있음
- **그럼에도 유효한 이유**: 공식 빌트인 기능이므로 서드파티 의존성 제거. 장기적으로 Anthropic이 직접 개선할 가능성 높음

### 주장 2: Mac Mini가 24/7 운용에 최적이다
- **틀릴 수 있는 조건**: 클라우드 VM(AWS, GCP 등)이 더 안정적이고 전원/네트워크 걱정 없음. 비용도 소형 인스턴스면 Mac Mini 전기세와 비슷할 수 있음
- **그럼에도 유효한 이유**: 로컬 파일 접근, 추가 비용 없음(이미 보유 시), 네트워크 지연 최소. 비기술자에게 클라우드보다 진입장벽 낮음

### 주장 3: SyncThing이 파일 동기화 최적 솔루션이다
- **틀릴 수 있는 조건**: Git으로 dotfiles 관리하는 것이 버전 관리 측면에서 우월. iCloud/Dropbox가 더 간편할 수 있음. 충돌 해결이 복잡해질 수 있음
- **그럼에도 유효한 이유**: 무료, P2P(클라우드 불필요), 실시간 동기화. Git은 수동 커밋 필요하고, 클라우드 스토리지는 심링크 문제 발생 가능

---

## 적용성 분석

**적용성 점수**: High

### 연결점
- 포트폴리오: 현재 think-tank 프로젝트에서 Claude Code + Telegram 채널을 이미 활용 중 (telegram:configure, telegram:access 스킬 보유)
- 의사결정: 다중 기기 간 Claude 환경 동기화 전략 수립에 직접 참고 가능
- 액션: LaunchAgent 자동 재시작 스크립트를 현재 환경에 바로 적용 가능

### 구체적 활용 방안
- **SyncThing 동기화 대상 목록**: ~/.claude/skills, commands, settings.json 동기화 시 참고할 체크리스트
- **LaunchAgent 패턴**: claude-channels-restart.sh + plist 구조를 현재 Telegram 봇 운영에 적용
- **동기화 제외 목록**: settings.local.json, history.jsonl, projects/ 폴더 제외 규칙 — 실수 방지용 참고자료

### work-manager 연동 제안
- 연동 필요: No
- 즉시 참고 가능한 운영 가이드 성격

---

## 원문 발췌 (중요 부분만)

> Claude Code Channels has no message queue. If Claude's session isn't running when you send a Telegram message, that message is gone. Not saved for later. Not waiting in line. Just lost.

> The path trick nobody mentions: Claude Code tracks your projects by the exact folder path on your computer. If your laptop uses /Users/nick/Projects/ but your Mini uses /Users/admin/Projects/, Claude gets confused. The fix: use the same username on both machines.

> Why LaunchAgent and not a cron job: Cron runs in a stripped-down environment that can't access your login credentials. Claude Code needs your authentication to work, and LaunchAgents run inside your user session where those credentials are available.

---

## 핵심 기술 자산 (스크립트)

### claude-channels-restart.sh
```bash
#!/bin/zsh
tmux kill-session -t claude-channels 2>/dev/null
sleep 2
tmux new-session -d -s claude-channels -c ~/Projects
tmux send-keys -t claude-channels "unset CLAUDECODE" Enter
tmux send-keys -t claude-channels "claude --channels plugin:telegram@claude-plugins-official" Enter
sleep 20
tmux send-keys -t claude-channels "Resume monitoring. Check channels for any messages." Enter
```

### LaunchAgent plist (com.claude.channels.plist)
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.claude.channels</string>
    <key>ProgramArguments</key>
    <array>
        <string>/bin/zsh</string>
        <string>-c</string>
        <string>~/.claude/scripts/claude-channels-restart.sh</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>StartCalendarInterval</key>
    <dict>
        <key>Hour</key>
        <integer>4</integer>
        <key>Minute</key>
        <integer>0</integer>
    </dict>
    <key>StandardOutPath</key>
    <string>/tmp/claude-channels.log</string>
    <key>StandardErrorPath</key>
    <string>/tmp/claude-channels.log</string>
</dict>
</plist>
```

---

