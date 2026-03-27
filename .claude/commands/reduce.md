# Reduce — Atomic 인사이트 추출

intake/ 의 seed 노트에서 개별 atomic 인사이트를 추출하여 notes/ 에 저장합니다.

---

## 트리거

- `ops/queue.yaml`에서 `phase: extract`, `status: pending` 인 태스크가 있을 때
- 사용자가 특정 intake 노트를 지정하여 "reduce 해줘"라고 요청할 때

---

## 실행 절차

### Step 0: 컨텍스트 로드
- `ops/derivation-manifest.md` 읽기 (도메인 어휘, 추출 카테고리)
- `ops/config.yaml` 읽기 (selectivity, max_claims_per_source)
- `ops/queue.yaml` 에서 처리할 태스크 확인

### Step 1: Seed 노트 읽기
- `intake/` 에서 해당 seed 노트를 읽음
- YAML frontmatter의 source, evidence_level, applicability 메타데이터 활용

### Step 2: Atomic 인사이트 추출

seed 노트의 주요 주장 분석 섹션에서 개별 인사이트를 식별합니다.

**추출 기준** (ops/derivation-manifest.md의 Extraction Categories 참조):
- 각 인사이트는 **하나의 주장, 패턴, 또는 방법론**만 포함
- Evidence level이 🔴(의견)인 주장은 제외하거나 `type: tension`으로 분류
- 반대 시나리오의 독립적인 인사이트도 추출 가능
- 적용성 분석의 구체적 활용 방안도 `type: methodology`로 추출 가능

**Selectivity gate** (config에 따라):
- strict: 🟢(사실)만 추출
- moderate: 🟢 + 🟡(해석) 추출 (기본값)
- permissive: 🟢 + 🟡 + 🟠(추정) 추출

**최대 추출 수**: `max_claims_per_source` (기본 10)

### Step 3: Duplicate 검출

각 추출된 인사이트에 대해:
1. `notes/` 폴더의 기존 노트 제목과 비교
2. 가능하다면 qmd semantic search로 유사도 확인
3. 중복이 발견되면 해당 인사이트를 건너뛰고 로그에 기록

### Step 4: Atomic 노트 생성

각 인사이트를 `notes/` 에 개별 파일로 저장합니다.

**파일명**: prose-sentence title (완결된 주장 문장)
- 예: `오케스트레이션 레이어는 에이전트 관리 복잡도를 줄인다.md`
- 예: `Fresh context per phase prevents attention degradation.md`
- 원본 기사 언어에 따라 한국어/영어 결정

**YAML frontmatter**:
```yaml
---
description: "타이틀을 보완하는 설명, ~150자. 타이틀에 없는 정보를 추가"
type: claim | methodology | problem | tension
created: YYYY-MM-DD
source_verification: "1차자료" | "2차해석" | "AI요약"
evidence_level: "fact" | "interpretation" | "assumption" | "opinion"
applicability: "High" | "Medium" | "Low"
topic: "topic-slug"
tags:
  - tag1
  - tag2
source_url: "원본 URL"
source_author: "저자명"
---
```

**본문**: 150-400자
- 주장의 핵심 근거와 추론을 서술
- 원문의 구체적 데이터나 사례 인용
- seed 노트의 evidence 라벨 정보 반영

**Footer**:
```markdown
---
Source:: [[intake 노트 파일명 (확장자 제외)]]
Topics:: [[Domain MOC 이름]]
```

### Step 5: Queue 업데이트

`ops/queue.yaml` 업데이트:
- 원래 extract 태스크의 status를 "completed"로 변경
- 각 생성된 atomic 노트에 대해 새 태스크 추가:
  ```yaml
  - id: "노트 파일명 (확장자 제외)"
    source: "notes/노트파일명.md"
    phase: "reflect"
    status: "pending"
    created: "YYYY-MM-DDTHH:MM:SS"
    parent: "원래 extract 태스크 id"
  ```

---

## 출력 요약

실행 완료 후 다음을 출력합니다:
- 추출된 인사이트 수
- 중복으로 건너뛴 수
- 생성된 파일 목록
- queue에 등록된 다음 단계 태스크 수
