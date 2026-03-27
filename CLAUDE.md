# Think-Tank Knowledge System

이 Vault는 Telegram에서 수집한 콘텐츠를 4단계 검증 후 atomic 인사이트로 분해하여 지식 그래프를 구축하는 시스템입니다.

## Three Spaces

| Space | 경로 | 용도 |
|-------|------|------|
| **Notes** | `notes/` | Atomic 인사이트 (1파일=1주장, [[wiki-link]]) |
| **Ops** | `ops/` | 파이프라인 상태, 큐, 설정 |
| **Memory** | `memory/` | 사용자 프로필, 스타일, 워크플로우 |

보조 공간: `intake/` (4단계 검증 seed 노트), `archive/` (원문 보존), `maps/` (MOC)

## Processing Pipeline

```
.inbox/ → Phase 1 (Verify) → intake/ seed
       → Phase 2 (Reduce)  → notes/ atomic insights
       → Phase 3 (Reflect + Reweave + Verify) → [[wiki-links]] + MOC updates
```

### Phase 1: Verify (4단계 검증)
`.claude/commands/intake/index.md` 참조. 출처/근거/반대시나리오/적용성 검증 후 intake/ 에 seed 노트 생성.

### Phase 2: Reduce (atomic 추출)
`.claude/commands/reduce.md` 참조. seed 노트에서 개별 인사이트를 추출하여 notes/ 에 저장.

### Phase 3: Reflect + Reweave + Verify (연결 생성)
`.claude/commands/reflect.md`, `reweave.md`, `verify.md` 참조.

## Note Design Rules

### Atomic Notes (notes/)
- **제목**: prose-sentence (완결된 주장 문장)
  - Good: `Progressive disclosure reduces cognitive load in complex interfaces.md`
  - Bad: `Progressive disclosure.md`
- **Composability test**: `since [[제목]]` 이 자연스럽게 읽혀야 함
- **YAML frontmatter**: description, type, created, topic, tags (필수)
- **Body**: 150-400자, 주장의 근거와 추론
- **Footer**: `Source::`, `Topics::` wiki-links

### Intake Notes (intake/)
- 기사 단위 요약 (seed). YAML frontmatter: title, source, url, date, topic, applicability, author, published, tags, type

### MOCs (maps/)
- 3-tier: Hub → Domain → Topic
- 섹션: Core Ideas (컨텍스트 문구 필수), Tensions, Open Questions
- Core Ideas 형식: `- [[노트 제목]] — 이 노트가 여기 속하는 이유`

## Discovery Patterns

1. **MOC traversal**: Hub → Domain MOC → 관련 노트 탐색
2. **Wiki-link graph**: Obsidian graph view로 연결 패턴 시각화
3. **qmd semantic search**: `collection: "obsidian-vault"` 에서 의미 기반 검색

## Configuration

- Pipeline 설정: `ops/config.yaml`
- 도메인 어휘: `ops/derivation-manifest.md`
- 큐 상태: `ops/queue.yaml`
- 사용자 컨텍스트: `CONTEXT.md`
- 메모리: `memory/` (my-style.md, workflows.md, decisions.md, tools.md)
