# work-manager ↔ Think Tank 연동 스킬

Think Tank에서 수집한 인사이트를 work-manager에 자동 연결하는 스킬입니다.

---

## Description

**트리거 조건**:
- `/intake` 스킬이 적용성 분석에서 업무 연관성을 감지했을 때
- 사용자가 "이거 work-manager에 추가해줘" 요청할 때

---

## 연동 프로세스

### 1. 업무 연관성 감지

적용성 분석에서 다음 조건 확인:
- 진행 중인 PRJ 카드와 연결점 있음
- "리서치", "설문", "분석", "인사이트" 등 키워드 포함
- 액션 가능한 방법론이나 사례

### 2. 관련 업무 카드 찾기

`CONTEXT.md`의 **§3 포트폴리오** 섹션에서 진행 중인 프로젝트 목록을 확인합니다. 필요 시 work-manager의 대시보드나 PRJ 카드 원본을 참조합니다.

매칭 로직:
- 인사이트 키워드 vs 업무 카드 제목/내용 유사도
- 토픽 vs 업무 카테고리 매칭
- 사용자 확인 필요 시 후보 2-3개 제시

### 3. 파일 복사

```bash
# 원본: ~/think-tank/intake/ux-research/2026-03-26-...md
# 복사: ~/Documents/ClaudeWorkspace/work-manager/references/external-insights/

cp [원본] [복사 위치]
```

### 4. 업무 카드 링크 추가

해당 PRJ 카드의 `## References` 섹션에 추가:
```markdown
## References
- [인사이트 제목](../../references/external-insights/ux-research-2026-03-26-...md) — Think Tank 연동 (2026-03-26)
```

### 5. 사용자 확인

```markdown
✅ work-manager 연동 완료

**연동된 인사이트**: [제목]
**관련 업무**: [PRJ-006] 픽업 브랜드 충성도 리서치
**저장 위치**: work-manager/references/external-insights/...

다음에 PRJ-006을 작업할 때 이 인사이트를 참고할 수 있습니다.
```

---

## 양방향 싱크

### work-manager → think-tank

**트리거**: `achievements/_index.md` 업데이트 시

**동작**:
1. achievements 새 행 감지
2. 성과 내용 요약 추출
3. `~/think-tank/CONTEXT.md`의 "포트폴리오" 섹션 자동 갱신

**실행 빈도**: 일 1회 (Cursor 세션 시작 시 체크)

### think-tank → work-manager

**트리거**: 적용성 분석에서 업무 연관 감지 시

**동작**:
1. 사용자에게 연동 제안
2. 승인 시 파일 복사
3. 업무 카드에 링크 추가

**실행 빈도**: 인사이트 저장 시마다

---

## 충돌 방지

### 중복 연동 체크
- 동일 URL의 인사이트가 이미 연동되어 있으면 스킵
- 파일명 중복 시 `-v2`, `-v3` 버전 번호 추가

### 수동 조정
사용자가 연동을 거부하거나 다른 카드로 연결하고 싶으면:
- `.intake-link-manual.json` 파일에 수동 매핑 저장
- 이후 자동 제안 시 이 매핑 우선 참조

---

## 연동 통계

연동 현황은 `work-manager/references/external-insights/README.md`에서 자동 갱신됩니다.

---

## 실행 예시

```markdown
## 💼 work-manager 연동 제안

이 인사이트가 다음 업무에 유용해 보입니다:

**[PRJ-004] NPS 데이터 처리 완전 자동화**
- 연결점: 텍스트 코딩 자동화 방법론
- 활용: MODULE 1 (학습 기반 코딩) 설계 참고

**[PRJ-005] AI 기반 설문 설계 에이전트**
- 연결점: AI 프롬프트 엔지니어링 사례
- 활용: 에이전트 프롬프트 개선

추가할까요? (yes / no / 다른 카드에 연결)
```

---

## 참고

- 이 스킬은 `/intake` 스킬 완료 후 자동 실행됩니다.
- 사용자 승인 없이 자동 연동하지 않습니다.
