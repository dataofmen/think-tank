# Verify — 스키마 + 품질 검증

atomic 노트의 스키마 준수 여부와 품질을 검증합니다.

---

## 트리거

- `ops/queue.yaml`에서 `phase: verify`, `status: pending` 인 태스크가 있을 때

---

## 실행 절차

### Test 1: Cold-Read Prediction (품질 검증)

1. 노트의 제목(파일명)과 description만 읽음
2. 본문 내용을 예측
3. 실제 본문과 비교
4. 점수 부여 (1-5):
   - 5: 제목+description으로 본문이 거의 정확히 예측됨
   - 4: 대부분 예측 가능, 약간의 추가 정보
   - 3: 핵심 방향은 맞지만 세부 내용이 다름 (최소 통과 기준)
   - 2: 제목이 본문을 제대로 반영하지 못함
   - 1: 제목과 본문이 거의 무관

**3점 미만이면**: 제목(파일명) 또는 description 수정을 제안

### Test 2: Schema Compliance (스키마 검증)

`ops/config.yaml`의 `note_schema.required_fields` 기준:

- [ ] YAML frontmatter 존재
- [ ] `description` 필드 존재 (제목에 없는 정보 추가, ~150자)
- [ ] `type` 필드 존재 (유효한 enum 값)
- [ ] `created` 필드 존재 (날짜 형식)
- [ ] `topic` 필드 존재 (유효한 topic slug)
- [ ] `tags` 필드 존재 (1개 이상)

**누락 필드가 있으면**: 자동으로 추가/수정

### Test 3: Link Health (연결 건강도)

- [ ] Source:: 의 wiki-link 대상이 실제 존재하는 파일인지
- [ ] Topics:: 의 wiki-link가 유효한 MOC를 가리키는지
- [ ] Related:: 의 wiki-link가 실제 존재하는 파일인지
- [ ] 최소 1개의 incoming link가 있는지 (MOC에서 링크됨)

**깨진 링크가 있으면**: 수정 또는 제거

### Test 4: MOC Integration (MOC 통합 확인)

- [ ] 해당 Domain MOC의 Core Ideas에 이 노트가 있는지
- [ ] 컨텍스트 문구가 bare link가 아닌 설명과 함께 있는지

**MOC에 없으면**: 자동으로 추가

---

## 검증 결과 처리

### 통과 (모든 테스트 pass)
- `ops/queue.yaml`에서 태스크 status를 "completed"로 변경
- 완료된 태스크를 tasks 목록에서 제거 (또는 completed로 마킹)

### 실패 (하나 이상의 테스트 fail)
- 자동 수정 가능한 것은 수정
- 자동 수정 불가능한 것은 `ops/observations/` 에 기록
- 수정 후 재검증

---

## 출력 요약

```
Verify: [노트 제목]
- Cold-read score: 4/5 ✅
- Schema: 6/6 fields ✅
- Links: 3/3 valid ✅
- MOC: integrated ✅
→ Status: PASSED
```
