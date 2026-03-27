# Think Tank Context

> 개인 AI 싱크탱크의 컨텍스트 파일입니다. 에이전트가 세션 시작 시 이 파일을 읽어 사용자 프로필과 현재 관심사를 파악합니다.

---

## 1. 나는 누구인가

### 기본 정보
- **역할**: 시니어 UX 리서처 (Senior UX Researcher)
- **조직**: 푸드/커머스 배달 IT 회사 (배달앱)
- **프로덕트**: B2C 모바일
- **사용 도구**: Condense, Qualtrics, Jira, Slack

### 업무 맥락 (work-manager 연동)
상세 업무 정보는 `/Users/hmkwon/Documents/ClaudeWorkspace/CONTEXT.md` 참조

---

## 2. 현재 관심 주제 (자동 갱신)

> 이 섹션은 intake/ 폴더의 최근 수집 현황을 기반으로 자동 업데이트됩니다.

### 지난 30일 수집 현황
- **UX Research**: 0건
- **AI Productivity**: 0건
- **Product Strategy**: 0건
- **Data Analysis**: 0건
- **Market Trends**: 0건
- **Business**: 0건
- **Tech**: 0건

*(최종 업데이트: 2026-03-26)*

---

## 3. 포트폴리오 & 진행 중인 프로젝트 (work-manager 연동)

> 이 섹션은 work-manager/achievements/_index.md와 진행 중인 PRJ 카드에서 자동 추출됩니다.

### 2026년 주요 성과
- **SUP-002**: 배보데 최소주문금액바 인지 검증 지원 — 신뢰 관계 구축, 스테이크홀더 극찬

### 진행 중인 프로젝트
- **PRJ-001**: CX eNPS 정기 조사
- **PRJ-002**: 인앱서베이 플랫폼화
- **PRJ-003**: 인앱서베이 솔루션 Qualtrics 유효성 검토
- **PRJ-004**: NPS 데이터 처리 완전 자동화 시스템 구축
- **PRJ-005**: AI 기반 설문 설계 에이전트
- **PRJ-006**: 픽업 브랜드 충성도 리서치

*(최종 업데이트: 2026-03-26)*

---

## 4. 진행 중인 의사결정

> memory/decisions.md 참조

*(현재 비어있음 — 인사이트 수집 후 자동 업데이트)*

---

## 5. 지식 인테이크 설정

자동 저장 기준, 4단계 검증 프로세스, work-manager 연동 트리거의 상세는 `.claude/commands/intake/index.md`를 참조하세요.

---

## 6. 세션 관리

### Layer 구조
- **Layer 1**: `memory/` — 압축되어도 살아남는 핵심 (매 세션 자동 로드)
- **Layer 2**: 이 파일 (`CONTEXT.md`) — 세션 시작 시 로드
- **Layer 3**: `sessions/` — 과거 대화 아카이브 (필요 시 참조)

### 자동 아카이빙 조건
- 대화 길이 10,000토큰 초과 시
- 지난 내용을 `sessions/YYYY-MM-DD-HHMM.md`로 저장
- 이 파일 §8에 링크 추가

---

## 7. 에이전트 규칙

### 세션 시작 시 (필수)
1. `CONTEXT.md` (이 파일) 읽기
2. `memory/` 아래 4개 파일 읽기:
   - `my-style.md` (글쓰기 스타일)
   - `workflows.md` (인풋 경로)
   - `decisions.md` (진행 중인 의사결정)
   - `tools.md` (사용 도구)
3. `.inbox/` 또는 `.processing/` 확인 (새 인풋 있는지)

### 인사이트 처리 시
`.claude/commands/intake/index.md` 스킬을 실행합니다.

---

## 8. 최근 세션

*(아직 세션 기록 없음)*

---

**생성일**: 2026-03-26 · **최종 업데이트**: 2026-03-26 · **다음 리뷰**: 2026-04-26
