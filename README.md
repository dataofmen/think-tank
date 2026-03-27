# README — Think Tank 폴더 구조

개인 AI 싱크탱크의 지식 저장소입니다.

---

## 📁 폴더 구조

```
~/think-tank/
├── CONTEXT.md                # 사용자 프로필 (Layer 2)
├── memory/                   # Layer 1: 압축 방지 핵심 기억
│   ├── my-style.md          # 글쓰기 스타일
│   ├── workflows.md         # 인풋 경로 정의
│   ├── decisions.md         # 진행 중인 의사결정
│   └── tools.md             # 도구 목록
├── intake/                   # 검증 완료된 인사이트
│   ├── ux-research/
│   ├── ai-productivity/
│   ├── product-strategy/
│   ├── data-analysis/
│   ├── market-trends/
│   ├── business/
│   └── tech/
├── sessions/                 # Layer 3: 과거 대화 아카이브
├── archive/                  # 오래된 자료
├── .inbox/                   # Bot → Claude 전달 (임시)
├── .processing/              # 처리 중 마커 파일
├── .processed/               # 처리 완료 아카이브
├── inbox-pdf/                # PDF 입력 폴더
└── .claude/commands/intake/  # 4단계 검증 스킬
```

---

## 🧠 3중 기억 구조 (Layer)

### Layer 1: memory/ (압축 방지)

**목적**: 대화가 길어져도 절대 잊지 않는 핵심

**포함 내용**:
- 글쓰기 스타일, 선호 톤
- 5가지 인풋 워크플로우
- 진행 중인 의사결정
- 사용 도구 목록

**자동 로드**: 에이전트가 매 세션 시작 시 읽음

### Layer 2: CONTEXT.md (세션 컨텍스트)

**목적**: "나는 누구" + "지금 뭘 하고 있는지"

**포함 내용**:
- 사용자 프로필 (역할, 조직, 관심사)
- 최근 30일 수집 현황
- 포트폴리오 (work-manager 자동 연동)
- 에이전트 규칙

**자동 업데이트**: 주 1회 또는 인사이트 10건 누적 시

### Layer 3: sessions/ (과거 대화)

**목적**: 필요 시 참조할 수 있는 아카이브

**자동 아카이빙**:
- 대화 길이 10,000토큰 초과 시
- `sessions/YYYY-MM-DD-HH-MM.md` 저장
- CONTEXT.md에 링크 추가

---

## 📝 인사이트 파일 형식

`intake/` 아래 모든 인사이트는 다음 형식:

```markdown
# [제목]

**출처**: [1차자료] / [2차해석] / [AI요약]
**URL**: ...
**수집일**: YYYY-MM-DD
**토픽**: ux-research

---

## 주요 주장 분석

1. 🟢 **[주장]**
2. 🟡 **[주장]**

---

## 반대 시나리오

...

---

## 적용성 분석

**적용성 점수**: High

### 연결점
- 포트폴리오: [PRJ-006]
- 액션: ...

---

## 메타데이터
- 태그: #ux #research
```

---

## 🔄 워크플로우

### Telegram → 자동 검증 → 저장

1. **모바일에서 링크 전송** (Telegram)
2. **Bot 수신 & 크롤링**
3. **`.inbox/pending-*.json` 생성**
4. **Cursor에서 `/intake` 스킬 실행**
5. **4단계 검증**
6. **자동 저장** (`intake/[토픽]/`)
7. **Telegram 알림** (검증 완료)

---

## 🔗 work-manager 연동

업무 관련 인사이트는 자동으로 work-manager에 연결:

```
~/think-tank/intake/ux-research/2026-03-26-...md
                ↓ (연동 제안)
~/Documents/ClaudeWorkspace/work-manager/references/external-insights/
```

---

## 🛠️ 유지보수

### 일일 (자동)
- .inbox/ 처리
- intake 카운트 업데이트

### 주간 (수동)
- 수집된 인사이트 리뷰
- 유용도 체크 (활용 안 된 것 archive/)

### 월간 (자동 + 수동)
- CONTEXT.md 통계 갱신
- 토픽 분류 정확도 리뷰
- memory/ 파일 업데이트 확인
