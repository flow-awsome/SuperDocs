# 외부 레퍼런스 정합성 검토

이 문서는 SuperDocs의 폴더 구조와 운영 원칙이 업계 표준, 공식 가이드, 검증된 실무 관행과 정합하는지 주제별로 검토한 근거를 담는다. 각 절은 해당 표준/관행의 내용과, 그로부터 이 하네스에 실제로 반영한 항목을 기록한다.

## 에이전트 하네스 공식 가이드라인

Claude Code 공식 문서는 상시 로드되는 프로젝트 규칙 파일("이 줄을 지우면 실수할까?"로 판정해 최소·고신호 토큰만 유지)과, 호출 시에만 로드되는 절차(Agent Skills)를 구분한다. Anthropic의 에이전트 설계 원칙은 단순한 방법이 실패할 때만 에이전트적 복잡성을 추가하도록 권고하며, 독립된 컨텍스트에서 diff와 기준만으로 판단하는 교차검증(subagent review) 방식을 제시한다.

참고: [code.claude.com/docs/en/best-practices](https://code.claude.com/docs/en/best-practices), [code.claude.com/docs/en/skills](https://code.claude.com/docs/en/skills), [anthropic.com/engineering/building-effective-agents](https://www.anthropic.com/engineering/building-effective-agents)

**반영**: [AGENTS.md](../AGENTS.md)의 가지치기 원칙, [11-audit](../11-audit/README.md)의 subagent 기반 교차검증 명문화, [04-system-instructions](../01-architecture/04-system-instructions/README.md)의 절차 분리 원칙.

## AI 코딩 도구의 프로젝트 컨텍스트 관례

Cursor, Aider, Windsurf, Devin, GitHub Copilot 등 주요 AI 코딩 도구는 프로젝트 컨텍스트를 스키마 없는 마크다운 파일로 관리하며, 규모가 커지면 단일 파일에서 경로별/스코프별 분할로 진화하는 공통 패턴을 보인다. `AGENTS.md`는 다수의 도구가 채택한 개방 표준으로 자리잡았으며, 저장소 **루트**에 두는 것이 관례다. Claude Code는 `AGENTS.md`를 직접 읽지 않으므로, `CLAUDE.md`가 `@AGENTS.md`를 import하는 방식이 권장된다.

참고: [agents.md](https://agents.md/), [factory.ai/news/agents-md](https://factory.ai/news/agents-md), [augmentedswe.com](https://www.augmentedswe.com/p/symlink-claudemd-agentsmd)

**반영**: 저장소 루트에 `AGENTS.md`(또는 `CLAUDE.md`가 이를 import)를 두고 상세본인 [docs/AGENTS.md](../AGENTS.md)로 링크하도록 [README.md](../../README.md) 적용 절차에 포함. 정적 규칙과 축적 메모리를 분리하는 관례는 이 하네스의 [07-decisions](../07-decisions/README.md)/[06-history](../06-history/README.md) 구조와 정합한다.

## 아키텍처 문서화 표준

arc42의 "본문(현재 상태) + 결정 기록(9장) + 별도 변경이력" 구조는 이 하네스의 [01-architecture](../01-architecture/README.md) + [07-decisions](../07-decisions/README.md) + [06-history](../06-history/README.md) 구조와 대응한다. C4 모델의 Context 레벨(외부 시스템·행위자 경계)과 arc42의 품질목표(quality goals) 절은 기존 구조에 명시적으로 존재하지 않았다. arc42·C4·4+1 어디에도 "AI 에이전트 운영 규칙" 항목은 없다.

참고: [arc42.org/overview](https://arc42.org/overview/), [docs.arc42.org/section-9](https://docs.arc42.org/section-9/), [4+1 아키텍처 뷰 모델](https://en.wikipedia.org/wiki/4+1_architectural_view_model)

**반영**: [service-boundary-map.md](../01-architecture/01-system-composition/service-boundary-map.md)에 외부 경계(Context 레벨) 절 추가, [00-system-foundation](../01-architecture/00-system-foundation/README.md)에 [quality-goals.md](../01-architecture/00-system-foundation/quality-goals.md) 신설, [01-architecture/README.md](../01-architecture/README.md)에 표준 대응관계 명시. [04-system-instructions](../01-architecture/04-system-instructions/README.md)는 이 표준들의 확장 범위 밖에 있는 이 하네스 고유 구성 요소임을 명시.

## 결정 기록 표준

ADR(Architecture Decision Record)의 원형은 배경·결정·트레이드오프를 다루는 간결한 구조였고, 이후 확장된 관행(MADR)은 옵션 비교에 앞서 "결정 동인(Decision Drivers)"을 명시하도록 요구한다. 업계 관행은 ADR을 구조적으로 유의미한 기술 결정에 한정하며, 일정·스코프·우선순위는 별도의 decision log로 다룬다.

참고: [cognitect.com — Documenting Architecture Decisions](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions.html), [adr.github.io/madr](https://adr.github.io/madr/), [AWS Prescriptive Guidance](https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/best-practices.html)

**반영**: ADR 템플릿 3종에 "결정 동인" 섹션 추가. [07-decisions/README.md](../07-decisions/README.md)에 [02-progress-decisions](../07-decisions/02-progress-decisions/README.md)가 업계 표준 ADR 정의 범위 밖의 확장임을 명기.

## 대규모 조직의 설계 합의 프로세스

Amazon의 PRFAQ, Google의 Design Doc, Rust RFC, Kubernetes KEP, Python PEP는 서로 독립적으로 다음 패턴에 수렴한다: 제안이 승인되면 원문은 동결하고 실행 추적은 별도 문서로 분리하며, 검토 과정에서 기각한 대안을 명시적으로 남기고, 문서 상단에 생애주기 상태를 표시한다.

참고: [industrialempathy.com — Design Docs at Google](https://www.industrialempathy.com/posts/design-docs-at-google/), [Rust RFC process](https://rust-lang.github.io/rfcs/), [PEP 1](https://peps.python.org/pep-0001/)

**반영**: [결정 인터뷰 템플릿](../10-consulting/02-decision-interviews/_template-decision-interview.md)에 기각된 옵션과 그 이유를 남기는 항목 추가.

## 문서 분류 이론

Diátaxis 프레임워크는 문서를 Tutorial(학습)·How-to(작업)·Reference(정보)·Explanation(이해) 4종으로 분류한다. 이 기준으로 SuperDocs의 폴더를 매핑하면 Tutorial에 해당하는 유형이 없고, Explanation은 개별 결정 기록에 국한되어 구조 전체를 아우르는 통합 설명이 부재했다.

참고: [diataxis.fr](https://diataxis.fr)

**반영**: [01-architecture/README.md](../01-architecture/README.md)에 구조 전체를 설명하는 절 추가.

## 테스트 및 검증 문서 표준

요구사항 추적 매트릭스, ISO/IEC/IEEE 29119의 테스트 문서 산출물 체계, 테스트 피라미드(단위/통합/E2E 비율)는 검증 활동을 문서화하는 데 널리 쓰이는 기준이다.

참고: [testrail.com — Requirements Traceability Matrix](https://www.testrail.com/blog/requirements-traceability-matrix/), [IEEE 29119-3](https://standards.ieee.org/ieee/29119-3/7499/)

**반영**: [05-test/README.md](../05-test/README.md)에 테스트 피라미드 목표 비율과 요구사항-검증 간 경량 추적 관례 추가.

## 인시던트 대응 문서 관행

Google SRE의 blameless postmortem 원칙은 사람이 아닌 시스템·프로세스에 초점을 맞추고, 재발 방지 항목에 담당자와 마감일을 명시하도록 요구한다. 포스트모템(원인·해결)과 변경 이력(사실의 시간순 기록)을 분리하는 것이 일반적인 관행이다.

참고: [sre.google/sre-book/postmortem-culture](https://sre.google/sre-book/postmortem-culture/)

**반영**: [트러블슈팅 템플릿](../08-troubleshooting/00-development-issues/_template-troubleshooting.md)에 담당자/마감일 필드, [08-troubleshooting/README.md](../08-troubleshooting/README.md)에 blameless 원칙과 반복 이슈 승격 규칙 추가.

## AI 에이전트 컨텍스트 관리 원칙

Anthropic이 제시하는 "context engineering" 원칙은 원하는 결과를 낼 수 있는 최소한의 고신호 토큰 집합을 유지하는 것을 핵심으로 삼는다. 컨텍스트가 길어질수록 정확도가 저하되는 현상("context rot")에 대한 독립 연구도 이를 뒷받침한다. 계층적 요약이 안전 제약을 유실시킬 수 있다는 지적("Compaction Cliff")도 함께 확인됐다.

참고: [anthropic.com/engineering/effective-context-engineering-for-ai-agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents), [trychroma.com/research/context-rot](https://www.trychroma.com/research/context-rot)

**반영**: [doc-governance-policy.md](doc-governance-policy.md)의 덮어쓰기/append-only 분리 원칙에 근거 인용 추가, 결정 기록·검증 기준을 요약 대상에서 제외하는 예외 조항 추가.

## 스펙 기반 개발 프레임워크 비교

spec-kit, BMAD-METHOD 등 스펙 기반/에이전트 네이티브 개발 프레임워크는 공통적으로 "에이전트가 내린 결정을 지속 가능한 컨텍스트로 고정하고 여러 도구가 재사용하게 만드는 문제"를 다룬다. 이들은 대개 모든 산출물의 기준점이 되는 단일 원칙 문서(constitution)를 두는 방식을 취한다.

참고: [github.com/github/spec-kit](https://github.com/github/spec-kit), [github.com/bmad-code-org/BMAD-METHOD](https://github.com/bmad-code-org/BMAD-METHOD)

**반영**: [mastery/01-docs-blueprint](../../mastery/01-docs-blueprint/README.md)의 프로젝트 정체성 요약 절이 이미 이 역할을 수행하고 있음을 명시.

## 검토 결과 요약

검토한 항목 중 다수 — 에이전트 하네스 공식 가이드라인, 아키텍처 문서화 표준, 결정 기록 표준, 인시던트 대응 문서 관행, AI 에이전트 컨텍스트 관리 원칙 — 는 기존 설계가 업계 표준 및 공식 가이드와 이미 정합함을 확인했다. 그 외 항목에서 확인된 구체적 격차는 각 절의 "반영" 항목에 따라 대상 문서에 직접 반영했다.

이 정합성 검토는 고정된 결론이 아니다. 업계 표준과 공식 가이드는 계속 갱신되므로, [11-audit](../11-audit/README.md) 정기 감사 시 이 문서의 유효성도 함께 재확인한다.
