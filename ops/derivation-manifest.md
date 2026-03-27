# Derivation Manifest — Think-Tank Knowledge System

## Domain

**Primary domain**: UX Research & AI Productivity Knowledge Management
**User**: Senior UX Researcher at a food/delivery company
**Language**: Korean + English bilingual (source language에 따라 노트 언어 결정)

## Vocabulary Mapping

| Ars Contexta Term | Think-Tank Term | 설명 |
|---|---|---|
| notes | notes | atomic 인사이트 저장소 |
| inbox | .inbox | Telegram bot이 pending JSON을 저장하는 곳 |
| archive | archive | 원문 보존 |
| seed | intake note | 4단계 검증 완료된 기사 단위 요약 |
| reduce | extract | seed에서 atomic 인사이트를 추출 |
| reflect | connect | 순방향 연결 — 새 노트 → 기존 노트 |
| reweave | update | 역방향 연결 — 기존 노트에 새 연결 추가 |
| verify | verify | 스키마 + 품질 검증 |
| rethink | review | 관찰과 긴장을 분류하고 승격 |
| topic map / MOC | map | 도메인별 네비게이션 구조 |
| observation | observation | 프로세스 개선점 |
| tension | tension | 노트 간 모순 |

## Extraction Categories

| Category | 추출 대상 | 예시 |
|---|---|---|
| Core UX insights | 리서치 방법론, 사용자 행동 패턴, 디자인 원칙 | "점진적 공개는 인지 부하를 줄인다" |
| AI workflow patterns | 에이전트 패턴, 프롬프트 엔지니어링, 자동화 기법 | "Phase별 fresh context가 주의력 저하를 방지한다" |
| Product strategy claims | 그로스, 리텐션, PMF, 포지셔닝 | "네트워크 효과는 임계 질량 이후 가속된다" |
| Data analysis methods | 통계, 측정, 실험 설계 | "A/B 테스트는 최소 검출 효과 크기 설정이 필요하다" |
| Market observations | 트렌드, 경쟁 역학, 산업 변화 | "플랫폼 경제는 규제 환경에 따라 전환된다" |
| Business patterns | 조직 설계, 리더십, 전략 | "교차기능팀은 명시적 권한 위임이 필요하다" |
| Tech architecture | 시스템 설계, 확장, 인프라 | "이벤트 기반 아키텍처는 결합도를 낮춘다" |

## Note Title Rules

- **Prose-sentence**: 주장을 완결된 문장으로 표현
- **Composability test**: `since [[제목]]` 이 자연스럽게 읽혀야 함
- **Claim test**: "이 노트는 [제목]을 주장한다" 가 말이 되어야 함
- **Language**: 원본 기사가 한국어면 한국어 제목, 영어면 영어 제목

## Topic Mapping

| Topic Slug | Domain MOC | Keywords |
|---|---|---|
| ux-research | [[UX Research]] | UX, 사용자경험, 리서치, 인터뷰, A/B test |
| ai-productivity | [[AI Productivity]] | AI, LLM, Claude, GPT, agent, automation |
| product-strategy | [[Product Strategy]] | PM, growth, retention, PMF, marketplace |
| data-analysis | [[Data Analysis]] | KPI, SQL, dashboard, experiment, 통계 |
| market-trends | [[Market Trends]] | 시장, 트렌드, TAM, forecast, 경쟁 |
| business | [[Business]] | 경영, 투자, OKR, 스타트업, leadership |
| tech | [[Tech]] | architecture, API, cloud, scaling, 인프라 |
