# Sync Portfolio to Think Tank

work-manager의 성과(achievements)와 진행 중인 프로젝트를 Think Tank CONTEXT에 자동 동기화하는 스킬입니다.

---

## Description

**트리거 조건**:
- Cursor 세션 시작 시 자동 실행 (일 1회)
- 사용자가 `/sync-portfolio` 명령어 입력 시

---

## 동기화 프로세스

### 1. work-manager에서 데이터 수집

#### 1.1 최근 성과 읽기
```bash
# 파일: ~/Documents/ClaudeWorkspace/work-manager/achievements/_index.md
```

추출 내용:
- 2026년 주요 성과 테이블
- 업무명, 핵심 임팩트

#### 1.2 진행 중인 프로젝트 읽기
```bash
# 파일: ~/Documents/ClaudeWorkspace/work-manager/_dashboard.md
# 또는: works/projects/PRJ-*.md (phase != "done")
```

추출 내용:
- PRJ ID, 제목, 현재 단계
- 목표, 완료 조건

### 2. Think Tank CONTEXT.md 업데이트

#### 2.1 "포트폴리오 & 진행 중인 프로젝트" 섹션 갱신

work-manager의 `achievements/_index.md`와 `_dashboard.md`에서 최신 데이터를 추출하여 `CONTEXT.md` §3을 갱신합니다. PRJ 목록은 하드코딩하지 않고 항상 work-manager 원본에서 동적으로 읽어옵니다.

#### 2.2 "현재 관심 주제" 섹션도 함께 갱신

```bash
# intake/ 폴더에서 지난 30일 통계 집계
find ~/think-tank/intake -name "*.md" -mtime -30 | wc -l
```

### 3. 변경 사항 로깅

```bash
# ~/think-tank/sessions/sync-log-YYYY-MM.md
```

```markdown
## 2026-03-26 포트폴리오 동기화

**변경 사항**:
- 진행 중 프로젝트: 6건 (변동 없음)
- 최근 성과: SUP-002 추가

**다음 동기화**: 2026-03-27
```

---

## 실행 빈도

- **자동**: 하루 1회 (Cursor 세션 첫 시작 시)
- **수동**: 사용자가 `/sync-portfolio` 입력 시
- **긴급**: work-manager에서 프로젝트 완료 시 즉시

---

## 충돌 방지

### 수동 편집 보호
- 사용자가 CONTEXT.md를 직접 수정했으면 덮어쓰지 않음
- "포트폴리오 섹션 업데이트할까요?" 물어봄

### 백업
- 업데이트 전 CONTEXT.md를 `CONTEXT.md.backup` 저장
- 문제 시 복구 가능

---

## 참고

- 이 스킬은 Cursor 세션 컨텍스트 복원 규칙에 통합되어 자동 실행됩니다.
- work-manager/CONTEXT.md의 §8 업데이트와 동기화됩니다.
