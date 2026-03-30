---
title: "How To Transform Claude Code Into A Self-Evolving System"
source: "X (Twitter)"
url: "https://x.com/meta_alchemist/status/2038222105654022325"
date: 2026-03-30
topic: "ai-productivity"
applicability: "High"
author: "meta_alchemist"
published: "2026-03-29"
tags:
  - ai-agent
  - self-evolving
  - claude-code
  - evolution-engine
  - memory-system
type: "article"
evidence_level: "fact"
source_verification: "1차자료"
---

# How To Transform Claude Code Into A Self-Evolving System

## 출처 메타데이터
- **원본 URL**: https://x.com/meta_alchemist/status/2038222105654022325
- **저자**: meta_alchemist (Seedify, Vibeship founder)
- **날짜**: 2026-03-29
- **타입**: X Article (전체 가이드)

## 원문 요약

meta_alchemist가 Claude Code를 self-evolving system으로 변환하는 방법에 대한 종합 가이드를 공개. 이 시스템은 AI가 매 세션마다 스스로를 개선하도록 설계되었다.

### 시스템의 4개 레이어

**Layer 1: Cognitive Core (CLAUDE.md)**
- 코드 작성 전 실행하는 결정 프레임워크
- Grep first, blast radius check, ask don't assume, smallest change, verification plan
- 완료 기준: typecheck, lint, test 모두 통과

**Layer 2: Specialized Agents**
- Architect: 복잡한 변경 계획 (read-only)
- Reviewer: 커밋 전 검증 (read-only)
- 각각 다른 툴 접근권한과 모델 티어

**Layer 3: Path-scoped Rules**
- security.md: API/auth 경로에서만 활성화
- api-design.md: 핸들러에서만 활성화
- performance.md: 모든 경로에서 활성화
- 컨텍스트 린 유지

**Layer 4: Evolution Engine**
- corrections.jsonl: 사용자 수정 기록
- observations.jsonl: 검증된 발견
- violations.jsonl: 룰 위반 로그
- sessions.jsonl: 세션 점수카드
- learned-rules.md: 승격된 패턴

### 진화 루프

**Correction Capture**: 사용자가 수정하면 → corrections.jsonl에 기록 → 같은 수정 2회 이상이면 learned-rules.md로 자동 승격

**Verification Sweep**: 세션 시작 시 learned-rules.md의 모든 verify: 체크 실행 → 위반 발견 시 즉시 알림

**Hypothesis-Driven Observations**: 패턴 발견 시 즉시 검증 → counter-example 확인 → 확정되면 자동으로 learned-rules.md 추가

**Session Scoring**: 세션 종료 시 점수카드 작성 → 트렌드 감지 (수정 감소? 시스템 작동 중)

## 주요 주장 분석

### 🟢 사실 (Facts)
- 4개 레이어 구조가 실제로 구현 가능
- verify: 라인을 통한 기계적 검증 체계 작동
- Correction → Observation → Learned Rule → Permanent Config 승격 사다리
- 메모리 파일들은 JSONL 포맷으로 저장
- learned-rules.md는 50줄 제한 (강제 졸업/가지치기)

### 🟡 해석 (Interpretations)
- Evolution Engine은 "면역 체계"로 작동: 검증, 강제, 학습 자동화
- verify 라인 없는 룰은 "wish", 있으면 "guardrail"
- 세션이 진행될수록 수정이 감소해야 시스템이 작동하는 것
- Path-scoped rules는 컨텍스트 효율성을 위한 핵심 설계

### 🟠 추정 (Assumptions)
- CLAUDE.md 150줄 이하 유지가 지침 준수율에 영향
- observations.jsonl과 corrections.jsonl은 느리게 성장 (세션당 5-10개)
- 커서리 규칙은 팀 지식으로 커밋, 개인 세션 데이터는 gitignore

### 🔴 의견 (Opinions)
- "자연스러운 선택이 작동한다. 유용한 패턴은 살아남고, 구식 규칙은 가지치기된다."
- "Auto-memory는 기억한다. 이 시스템은 강제한다."

## 반대 시나리오
- verify 패턴이 너무 엄격하면 false positive 위반 남발
- learned-rules.md가 너무 많아지면 세션 시작 검증이 느려짐
- 프로젝트별 규칙이 충돌할 수 있음 (서로 다른 스타일)
- 150줄 제한이 프로젝트 복잡도에 따라 부적절할 수 있음

## 적용 가능성
**High** - Think Tank 시스템의 ops/queue.yaml과 memory/ 구조와 유사한 진화 엔진 개념. Autoresearch 패턴과 결합 가능.

## 관련 노트
- [[Autoresearch pattern requires a measurable metric, code access, and experiment history tracking]] - 동일한 실험-평가-개선 루프
- [[Recursive evaluation-improvement loops raised AI agent first-pass quality from 40 percent to 94 percent]] - Sparkwave의 evaluation layer와 유사한 verify 체크
- [[Separating evaluation systems from generation layers enables continuous autonomous quality improvement]] - Evolution Engine은 evaluation layer 역할

## 원문 보존

전체 가이드는 약 1200줄의 종합적인 튜토리얼로, CLAUDE.md 템플릿, settings.json, rules/, agents/, skills/, memory/ 디렉토리 구조를 모두 포함.

**핵심 파일 구조:**
```
your-project/
├── CLAUDE.md                    # Cognitive core
└── .claude/
    ├── settings.json            # Permissions
    ├── rules/                   # Path-scoped intelligence
    │   ├── core-invariants.md
    │   ├── security.md
    │   ├── api-design.md
    │   └── performance.md
    ├── agents/                  # Specialized subagents
    │   ├── architect.md
    │   └── reviewer.md
    ├── skills/                  # Workflows
    │   ├── evolve/SKILL.md
    │   ├── review/SKILL.md
    │   ├── boot/SKILL.md
    │   ├── fix-issue/SKILL.md
    │   └── evolution/SKILL.md
    └── memory/                  # Learning infrastructure
        ├── learned-rules.md
        ├── evolution-log.md
        ├── corrections.jsonl
        ├── observations.jsonl
        ├── violations.jsonl
        └── sessions.jsonl
```

**Verification 패턴 예시:**
```yaml
- Never use the spread pattern to merge options in fetchJSON.
  verify: Grep("\.\.\.options", path="src/api/client.js") → 0 matches
  [source: corrected 2x, 2026-03-28]
```

---
*meta_alchemist의 완전한 가이드는 Claude Code를 self-evolving system으로 변환하는 방법을 단계별로 제공. 핵심은 correction → verification → rule 승격 루프가 자동으로 작동하도록 설계하는 것.*