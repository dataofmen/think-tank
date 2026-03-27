---
description: "Anthropic의 Filesystem MCP 서버가 로컬 파일 경로 지정만으로 Claude Desktop에서 Obsidian vault 읽기/쓰기를 가능하게 하며, Obsidian 측 플러그인이나 API 서버가 불필요하다."
type: methodology
created: 2026-03-27
source_verification: "2차해석"
evidence_level: "fact"
applicability: "High"
topic: "ai-productivity"
tags:
  - obsidian
  - mcp
  - claude
  - filesystem
  - pkm
source_url: "https://x.com/laozhang2579/status/2037106215747280968"
source_author: "老张来了 (@laozhang2579)"
---

Obsidian vault는 본질적으로 마크다운 파일 폴더이므로 Obsidian 전용 API 없이 파일시스템 레벨 접근만으로 읽기·쓰기·검색이 가능하다. Anthropic이 공식 제공하는 Filesystem MCP 서버를 활용하면 Claude Desktop의 설정 JSON에 vault 경로 하나만 추가하여 연동이 완료된다. 별도 플러그인 설치, REST API 서버 구동, 워크플로우 자동화 도구 연결 등 추가 의존성이 전혀 없다. 이는 [[The bottleneck for AI agent capability was deployment infrastructure not model intelligence|AI 에이전트의 실질적 병목이 배포 인프라]]라는 통찰의 구체적 사례로, 인프라 장벽을 최소화하면 AI-PKM 통합의 진입점이 극적으로 낮아진다. 다수의 오픈소스 프로젝트(mcp-obsidian 등)에서도 동일한 파일시스템 접근 패턴이 검증되었다. 다만 이 단순함은 [[Filesystem-only AI access to knowledge bases hits context window limits at scale requiring structured metadata layers|규모 확장 시 컨텍스트 윈도우 한계]]와 긴장 관계에 있다.

---
Source:: [[2026-03-27-ai-productivity-claude-obsidian-filesystem-mcp]]
Topics:: [[AI Productivity]]
