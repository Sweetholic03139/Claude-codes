# Claude-codes — Academic Research Skills 적용

이 저장소에는 [Imbad0202/academic-research-skills](https://github.com/Imbad0202/academic-research-skills) v3.21.2가
**프로젝트 스킬** 방식(공식 SETUP.md Method 1)으로 설치되어 있습니다.

## 구성

| 경로 | 내용 |
|---|---|
| `.claude/skills/deep-research/` | 13-에이전트 심층 연구 팀 (문헌 조사, 체계적 문헌고찰, 팩트체크 등 8개 모드) |
| `.claude/skills/academic-paper/` | 12-에이전트 논문 작성 (초안, 개요, 수정, 초록, 인용 검증 등) |
| `.claude/skills/academic-paper-reviewer/` | 다관점 동료 심사 (7-에이전트 리뷰 팀) |
| `.claude/skills/academic-pipeline/` | 전체 파이프라인 오케스트레이터 (연구 → 작성 → 심사 → 수정 → 마무리) |
| `.claude/skills/experiment-agent/` | 실험 실행·모니터링 ([experiment-agent](https://github.com/Imbad0202/experiment-agent) v1.0 — run/manage/validate/plan 모드, ARS Stage 1↔2 연계) |
| `.claude/commands/` | `/ars-plan`, `/ars-lit-review`, `/ars-full` 등 슬래시 커맨드 |
| `.claude/agents/` | 공용 에이전트 정의 |
| `.claude/CLAUDE.md` | 스킬 라우팅 규칙 |
| `shared/`, `scripts/`, `MODE_REGISTRY.md` | 스킬이 참조하는 공용 프로토콜·스크립트·모드 정의 |

## 사용법

이 저장소에서 Claude Code 세션을 열고 자연어로 요청하면 스킬이 자동 라우팅됩니다:

```
심층 연구: "저출산이 사립대학에 미치는 영향을 연구해줘"
논문 작성: "X 주제로 논문 개요를 잡아줘" 또는 /ars-plan
문헌 조사: /ars-lit-review "연구 주제"
동료 심사: "이 논문 초안을 리뷰해줘"
전체 파이프라인: /ars-full
```

## Rhino MCP (로컬 전용)

Rhino MCP 서버는 저장소(`.mcp.json`)가 아니라 **각 컴퓨터의 사용자 설정**(`~/.claude.json`)에
등록합니다. **Rhino가 실행 중인 로컬 컴퓨터에서만 동작합니다** — 웹(claude.ai/code) 세션의
클라우드 컨테이너는 로컬 Rhino에 접근할 수 없습니다.

로컬 사용 절차:

1. Rhino 8 또는 9에서 `PackageManager` 명령 실행 → `Rhino-MCP-Platform` 설치 → Rhino 재시작
2. Rhino에서 `MCPConnect` 명령 실행 → Install 탭에서 Claude Code 옆 **Install** 클릭
3. 이 저장소 폴더에서 `claude` 실행 → `/mcp` 목록의 User MCPs에 `rhino`가 연결됨으로 표시됨
4. "내 Rhino 문서에 뭐가 있어?" / "1.6m 벤치를 모델링해줘" 등 자연어로 사용

> 예전 버전의 이 저장소에는 `http://localhost:10500/`을 가리키는 `.mcp.json`이 있었습니다.
> 이 프로젝트 설정이 MCPConnect가 등록한 사용자 설정보다 우선 적용되어 `ECONNREFUSED`가 나므로
> 삭제했습니다. 로컬에 남아 있다면 `claude mcp remove rhino -s project`로 지우세요.

슬래시 커맨드·전문 에이전트(rhino-modeller, grasshopper-scripter 등)까지 쓰려면 로컬 세션에서
공식 플러그인을 설치하세요: `/plugin marketplace add mcneel/RhinoMCP` → `/plugin install mcneel@rhino-mcp`

## 라이선스

포함된 Academic Research Skills 콘텐츠는 CC BY-NC 4.0 라이선스를 따릅니다
(`LICENSE`, `NOTICE.md` 참조). 저작자: Cheng-I Wu (@Imbad0202).
