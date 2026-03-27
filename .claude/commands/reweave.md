# Reweave — 역방향 연결 업데이트

"이 노트를 오늘 모든 지식을 알고 있는 상태에서 다시 쓴다면 무엇이 달라질까?"

기존 노트들을 새 노트의 관점에서 재검토하고 업데이트합니다.

---

## 트리거

- `ops/queue.yaml`에서 `phase: reweave`, `status: pending` 인 태스크가 있을 때

---

## 실행 절차

### Step 0: 컨텍스트 로드
- 대상 노트와 reflect에서 발견된 연결 노트들 읽기
- 해당 Domain MOC 읽기

### Step 1: 역방향 스캔

Reflect에서 연결된 기존 노트들을 하나씩 검토:

**5가지 가능한 액션:**

1. **Add connection** — 기존 노트에 새 노트로의 wiki-link 추가
   - 기존 노트의 본문이나 Related:: 에 `[[새 노트]]` 링크 추가

2. **Sharpen claim** — 새 근거로 기존 노트의 주장을 더 정확하게
   - 기존 노트의 description이나 본문을 약간 수정

3. **Challenge claim** — 새 노트가 기존 노트와 모순되면
   - 기존 노트에 "그러나 [[새 노트]]에 의하면..." 추가
   - `ops/tensions/` 에 tension 파일 생성

4. **Split note** — 기존 노트가 사실은 2개의 주장을 담고 있었다면
   - 기존 노트를 2개로 분리 (드물게 발생)

5. **No action** — 연결은 있지만 기존 노트 수정이 불필요

### Step 2: 실행

각 액션을 실행합니다. 변경된 파일 목록을 기록합니다.

**주의**: 기존 노트의 핵심 주장(제목)은 변경하지 않습니다. 본문과 연결만 업데이트합니다.

### Step 3: Queue 업데이트

`ops/queue.yaml`에서 이 태스크의:
- phase를 "verify"로 변경
- status를 "pending"으로 유지
- reweave_actions 수를 기록

---

## Tension 파일 형식

모순 발견 시 `ops/tensions/` 에 저장:

```markdown
---
created: YYYY-MM-DD
status: open
---

# [[노트 A]] vs [[노트 B]]

**충돌**: A는 X를 주장하지만, B는 Y를 주장한다.
**조건**: A가 맞는 조건 vs B가 맞는 조건
**해결 방향**: 추가 조사 필요 / 맥락에 따라 다름 / 더 최신 근거가 우선
```
