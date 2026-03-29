---
description: "AI 도구, 에이전트 패턴, 자동화 워크플로우에 대한 인사이트 맵"
type: domain-moc
created: 2026-03-27
topic: "ai-productivity"
---

# AI Productivity

## Core Ideas

- [[Autoresearch agent discovered optimizations in nanochat that a 20-year expert had missed]] — AI 에이전트의 exhaustive search가 인간 전문가의 직관적 튜닝을 보완한 실증 사례
- [[Autoresearch agents plan next experiments based on previous results, not random search]] — NAS와 달리 LLM 기반 에이전트는 실험 결과를 분석하여 적응적으로 탐색 방향을 조정
- [[Competitive pressure will drive all frontier labs to adopt autoresearch agents]] — 11% 수준의 성능 개선이 경쟁 환경에서 채택을 강제하는 동력
- [[Any efficiently evaluable metric can be autoresearched by an agent swarm]] — 효율적 프록시 메트릭이 존재하면 에이전트 스웜으로 자동 최적화 가능
- [[Autoresearch pattern requires a measurable metric, code access, and experiment history tracking]] — autoresearch의 핵심 패턴을 메트릭/코드접근/실험이력 3요소로 추상화
- [[Recursive evaluation-improvement loops raised AI agent first-pass quality from 40 percent to 94 percent]] — evaluation-generation 분리 아키텍처에서 자동 품질 개선 루프가 40%→94% 달성한 실증 사례
- [[Separating evaluation systems from generation layers enables continuous autonomous quality improvement]] — evaluation/generation 분리가 자율 품질 개선의 아키텍처적 전제조건
- [[The bottleneck for AI agent capability was deployment infrastructure not model intelligence]] — AI 에이전트의 실질적 병목은 모델 지능이 아닌 배포 인프라였으며 오픈소스로 해소 중
- [[AI agents that use their own capabilities to build new capabilities produce compound improvement effects]] — 에이전트 자체 역량이 다음 개선 사이클의 인프라가 되는 복리 효과
- [[A Mac Mini and Telegram bot can run a personal AI agent system 24-7 for months without reliability issues]] — 소비자 하드웨어로 2개월간 24/7 에이전트를 안정 운영한 실증 사례
- [[Migrating between AI agent orchestration frameworks takes hours not days when the infrastructure layer is stable]] — 인프라 레이어 분리로 3시간 내 프레임워크 마이그레이션을 완료한 사례
- [[Automated morning briefings from multiple sources compress hours of daily research scanning into minutes]] — 다중 소스 자동 수집→필터링→브리핑 파이프라인이 리서치 스캐닝 시간을 대폭 단축
- [[A twenty-dollar-per-month LLM is sufficient to power a practical daily-use AI agent system]] — $21/월 GLM-5로 실용적 에이전트를 2개월간 운영한 비용 효율 사례
- [[Filesystem MCP connects Claude Desktop to Obsidian vaults through a single JSON config without plugins]] — JSON 설정 하나로 Obsidian vault를 Claude에 연동하는 최소 인프라 패턴
- [[Unnecessary complexity in AI-PKM integration reduces actual adoption more than it adds capability]] — AI-PKM 통합에서 초기 마찰 제거가 기능 풍부성보다 장기 활용도를 결정
- [[Filesystem-only AI access to knowledge bases hits context window limits at scale requiring structured metadata layers]] — 파일시스템 단독 접근의 규모 확장 한계와 구조화된 메타데이터 필요성
- [[Chaining NotebookLM Claude and Anki produced 504 flashcards from a single TV series without textbooks]] — NotebookLM→Claude→Anki 3단계 체이닝으로 TV 시리즈에서 504장 플래시카드를 자동 생성한 사례
- [[FSRS algorithm trained on 700 million reviews optimizes spaced repetition beyond traditional schedulers]] — 7억 건 커뮤니티 데이터로 훈련된 ML 기반 간격 반복 스케줄러가 전문가 설계 SM-2를 초월
- [[Emotional anchoring from familiar media content improves vocabulary retention over context-free methods]] — 친숙한 미디어의 감정적 맥락이 탈맥락적 어휘 학습보다 기억 유지율을 높인다는 인지심리학 기반 주장
- [[Multi-AI tool chaining outperforms single tools by assigning specialized strengths to each pipeline stage]] — 추출→변환→실행 각 단계에 특화 AI를 배치하는 체이닝 패턴의 일반화

## Tensions

- [[Unnecessary complexity in AI-PKM integration reduces actual adoption more than it adds capability]] vs [[Filesystem-only AI access to knowledge bases hits context window limits at scale requiring structured metadata layers]] — 단순함이 채택을 높이지만, 규모에서는 구조적 복잡성이 불가피

## Open Questions

---
Parent:: [[Hub]]
