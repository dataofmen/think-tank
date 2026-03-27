# Reflect — 순방향 연결 생성

새로 생성된 atomic 노트에서 기존 노트로의 연결을 탐색하고, MOC를 업데이트합니다.

---

## 트리거

- `ops/queue.yaml`에서 `phase: reflect`, `status: pending` 인 태스크가 있을 때

---

## 실행 절차

### Step 0: 컨텍스트 로드
- 대상 노트 읽기
- `maps/` 에서 해당 topic의 Domain MOC 읽기
- `ops/derivation-manifest.md` 읽기

### Step 1: Dual Discovery

두 가지 방법으로 연결 대상을 탐색합니다:

**1. MOC Traversal (구조적 탐색)**
- 해당 topic의 Domain MOC에 이미 있는 노트들을 확인
- Hub MOC에서 다른 도메인의 관련 노트도 탐색
- Core Ideas 섹션의 컨텍스트 문구를 읽어 연결 가능성 판단

**2. Semantic Search (의미 기반 탐색)**
- qmd MCP가 가능하면: `collection: "obsidian-vault"` 에서 노트 제목/내용으로 검색
- 불가능하면: `notes/` 폴더의 파일명(제목)을 스캔하여 키워드 매칭

### Step 2: Articulation Test

발견된 각 연결에 대해 **왜** 연결되는지 명시합니다:

- "extends X by adding Y" — 확장
- "contradicts X because Y" — 모순 (→ tension으로 기록)
- "applies X to domain Y" — 적용
- "generalizes X across Y" — 일반화
- "provides evidence for X" — 근거 제공

**연결이 "관련됨" 이상으로 설명할 수 없으면 연결하지 않습니다.**

### Step 3: 노트에 Wiki-link 추가

대상 노트의 본문에 자연스럽게 `[[연결 노트]]` wiki-link를 삽입합니다.
- 본문 서술 중 관련 개념이 언급되는 곳에 인라인으로 삽입
- 또는 Footer의 `Related::` 섹션에 컨텍스트 문구와 함께 추가:
  ```markdown
  Related:: [[연결 노트]] — 연결 이유
  ```

### Step 4: MOC 업데이트

해당 Domain MOC의 Core Ideas 섹션에 새 노트를 추가합니다:
```markdown
- [[노트 제목]] — 이 노트가 이 도메인에 속하는 이유 한 줄
```

**Tension 발견 시**: MOC의 Tensions 섹션에 기록:
```markdown
- [[노트 A]] vs [[노트 B]] — 무엇이 충돌하는지
```

### Step 5: Queue 업데이트

`ops/queue.yaml`에서 이 태스크의:
- phase를 "reweave"로 변경
- status를 "pending"으로 유지
- reflect_connections 수를 기록

---

## 제약 사항

- 노트 1개당 연결은 최대 5개 (과도한 연결 방지)
- 자기 자신과의 연결 금지
- 같은 source에서 추출된 형제 노트끼리의 연결은 1개까지만
