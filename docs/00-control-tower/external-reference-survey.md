# 외부 레퍼런스 조사 — 근거 보강 (2026-09-12)

> 오너: PMO/거버넌스 · 마지막 확인: 2026-09-12 · 상태: 현재

## 이 문서가 존재하는 이유

이 하네스의 최초 설계 근거는 단일 사례(8개월 진행 중인 엔터프라이즈 프로젝트 1개, 약 500개 md 파일 감사)뿐이었다. 사례 하나에만 기대면 그 프로젝트의 특수성에 매몰되고, 우리가 놓친 대안을 보지 못할 위험이 있다. 이를 보완하기 위해 10개 조사팀을 병렬로 파견해 서로 다른 각도에서 외부 레퍼런스를 조사했다. 모든 팀에게 "최신 유행이 아니라 시간이 지나도 유효한 근본 원칙"을 우선하도록 지시했다.

이 문서는 10개 조사 결과의 원문 요약과, 그로부터 실제로 채택/변형/기각한 항목의 인덱스다. 개별 반영 내용의 상세는 각 대상 문서에 있다 — 여기서는 "무엇을 근거로 왜 그렇게 했는지"만 추적한다.

## 조사 1 — Anthropic 공식 하네스 기초

- **핵심 발견**: CLAUDE.md는 "지우면 Claude가 실수할까?"로 매 줄을 판정해 최소·고신호 토큰만 남겨야 한다. Agent Skills는 지연 로딩(description만 상주, 본문은 호출 시에만 로드) 구조라 "절차가 길어지면 스킬로 분리하라"는 명확한 전환 기준이 있다. Subagent는 독립 컨텍스트에서 diff+기준만 보고 판단하는 adversarial review에 적합.
- 출처: [code.claude.com/docs/en/best-practices](https://code.claude.com/docs/en/best-practices), [code.claude.com/docs/en/skills](https://code.claude.com/docs/en/skills), [anthropic.com/engineering/building-effective-agents](https://www.anthropic.com/engineering/building-effective-agents), [anthropic.com/engineering/effective-context-engineering-for-ai-agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
- **반영**: [AGENTS.md](../AGENTS.md) 가지치기 원칙, [11-audit](../11-audit/README.md) subagent 명문화, "문서 많을수록 안전하다"는 가정 명시적 기각.

## 조사 2 — 경쟁 AI 코딩 에이전트의 프로젝트 컨텍스트 관례

- **핵심 발견**: Cursor(.cursorrules → .cursor/rules/*.mdc), Aider(CONVENTIONS.md), Windsurf(정적 rules vs 축적 memory 분리), Devin(Knowledge vs Playbook 분리), GitHub Copilot(.github/copilot-instructions.md) 모두 "스키마 없는 순수 마크다운 + 규모 커지면 스코프 분할"로 수렴한다. 특히 **agents.md**가 Linux Foundation 산하로 이관되어 60,000+ 리포/30+ 도구가 채택한 개방 표준이 됐다 — 단, Claude Code는 AGENTS.md를 네이티브로 읽지 않고 CLAUDE.md만 읽으므로, 공식 권장 패턴은 `CLAUDE.md`가 `@AGENTS.md`를 import하는 것이다.
- 출처: [agents.md](https://agents.md/), [factory.ai/news/agents-md](https://factory.ai/news/agents-md), [augmentedswe.com — symlink CLAUDE.md/AGENTS.md](https://www.augmentedswe.com/p/symlink-claudemd-agentsmd)
- **반영**: 이 저장소를 실제 프로젝트에 적용할 때 저장소 루트에 `AGENTS.md`(또는 `CLAUDE.md`가 이를 import)를 두고 상세본인 `docs/AGENTS.md`로 링크하도록 [README.md](../../README.md) 적용 절차에 단계 추가. rules(정적)/memory(축적) 분리는 이미 [07-decisions](../07-decisions/README.md) vs [06-history](../06-history/README.md) 구조로 동형이라 변경 불필요.

## 조사 3 — 아키텍처 문서화 표준 (arc42 / C4 / 4+1)

- **핵심 발견**: arc42의 "본문(현재 상태) + 9장 ADR(왜) + 별도 변경이력" 3분리가 [01-architecture](../01-architecture/README.md) + [07-decisions](../07-decisions/README.md) + [06-history](../06-history/README.md) 구조와 정확히 대응한다. C4 모델의 Context 레벨(외부 시스템/행위자 경계)이 [01-system-composition](../01-architecture/01-system-composition/README.md)에 빠져 있었다. arc42/C4/4+1 어디에도 "AI 에이전트 운영 규칙" 항목은 없다 — [04-system-instructions](../01-architecture/04-system-instructions/README.md)는 이 하네스의 고유 확장이다.
- 출처: [arc42.org/overview](https://arc42.org/overview/), [docs.arc42.org/section-9](https://docs.arc42.org/section-9/), [c4model.com 관련](https://lucid.co/blog/c4-model), [4+1 뷰 모델](https://en.wikipedia.org/wiki/4+1_architectural_view_model)
- **반영**: [service-boundary-map.md](../01-architecture/01-system-composition/service-boundary-map.md)에 외부 시스템/행위자 경계 절 추가, [00-system-foundation](../01-architecture/00-system-foundation/README.md)에 품질목표 문서 신설, [01-architecture/README.md](../01-architecture/README.md)에 표준 대응관계 명시.

## 조사 4 — ADR 생태계

- **핵심 발견**: Nygard 원전(2011)은 5개 섹션(Title/Status/Context/Decision/Consequences)뿐이었고, MADR이 "결정 동인(Decision Drivers)"과 옵션별 장단점을 추가했다. AWS/ThoughtWorks 모두 "구조적으로 유의미한 기술 결정"에만 ADR을 한정하며, [02-progress-decisions](../07-decisions/02-progress-decisions/README.md)처럼 일정/스코프/우선순위를 ADR 포맷으로 다루는 업계 선례는 발견되지 않았다 — 이는 SuperDocs의 독자적 확장이다. log4brains는 전역 순번 대신 날짜 접두 파일명으로 병렬 작성 시 병합 충돌을 피한다.
- 출처: [Nygard 원문](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions.html), [MADR](https://adr.github.io/madr/), [AWS Prescriptive Guidance](https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/best-practices.html), [ThoughtWorks Radar](https://www.thoughtworks.com/en-us/radar/techniques/lightweight-architecture-decision-records), [log4brains](https://github.com/thomvaill/log4brains)
- **반영**: ADR 템플릿 3종에 "결정 동인" 섹션 추가, [07-decisions/README.md](../07-decisions/README.md)에 02-progress-decisions가 업계 표준 ADR 정의 밖의 확장임을 명기.

## 조사 5 — 대규모 조직의 설계 합의 문서 문화

- **핵심 발견**: Amazon PRFAQ, Google Design Doc, Rust RFC, Kubernetes KEP, Python PEP가 독립적으로 수렴한 패턴: (a) 제안 승인 후 원문은 동결하고 실행 추적은 별도 문서(tracking issue/step-log)로 분리, (b) "고려했으나 기각한 대안"을 반드시 문서화, (c) 문서 상단에 명시적 생애주기 상태 태그.
- 출처: [workingbackwards.com](https://workingbackwards.com/concepts/working-backwards-pr-faq-process/), [industrialempathy.com — Design Docs at Google](https://www.industrialempathy.com/posts/design-docs-at-google/), [Rust RFC process](https://rust-lang.github.io/rfcs/), [Kubernetes KEP process](https://github.com/kubernetes/enhancements/blob/master/keps/sig-architecture/0000-kep-process/README.md), [PEP 1](https://peps.python.org/pep-0001/)
- **반영**: [_template-decision-interview.md](../10-consulting/02-decision-interviews/_template-decision-interview.md)에 기각 옵션 보존 명시. Google식 정기 라이브 리뷰 회의체는 소규모 팀엔 과해 기각.

## 조사 6 — Diátaxis 문서화 이론

- **핵심 발견**: Tutorial/How-to/Reference/Explanation 4분류 기준으로 SuperDocs 12폴더를 매핑하면, Tutorial은 전무하고 Explanation은 [07-decisions](../07-decisions/README.md)(개별 ADR)에만 갇혀 "이 구조가 전체적으로 왜 이런 모양인가"를 설명하는 통합 서술이 없다.
- 출처: [diataxis.fr](https://diataxis.fr), [Python.org — Adopting Diátaxis 토론](https://discuss.python.org/t/adopting-the-diataxis-framework-for-python-documentation/15072)
- **반영**: [01-architecture/README.md](../01-architecture/README.md)에 "왜 이렇게 구성됐는가" 통합 explanation 절 추가. 06/09/10 폴더를 억지로 4종에 끼워 맞추지는 않음(SuperDocs 고유 "운영 메타" 축으로 유지).

## 조사 7 — 테스트/검증 문서 표준

- **핵심 발견**: RTM(요구사항 추적 매트릭스), ISO/IEC/IEEE 29119(Test Plan~Completion Report 산출물), 테스트 피라미드(성숙한 팀 기준 unit 70% / integration 20% / e2e 10%), ISO 25010 품질모델 기반 비기능요구 세분화가 업계 표준.
- 출처: [testrail.com — RTM](https://www.testrail.com/blog/requirements-traceability-matrix/), [IEEE 29119-3](https://standards.ieee.org/ieee/29119-3/7499/), [Qase — Testing Pyramid](https://qase.io/blog/the-testing-pyramid-decoded/)
- **반영**: [05-test/README.md](../05-test/README.md)에 요구사항↔검증케이스 경량 추적 표, 테스트 피라미드 목표 비율 명시.

## 조사 8 — 인시던트/트러블슈팅 지식 문화 (SRE)

- **핵심 발견**: Google SRE의 blameless postmortem(시스템/프로세스에 초점, 담당자+마감일 붙은 액션 아이템), runbook은 인시던트 직후 온콜이 초안 작성, SEV 등급이 대응 속도를 결정. [08-troubleshooting](../08-troubleshooting/README.md)(사실+해결) vs [06-history](../06-history/README.md)(타임라인) 분리는 이미 업계의 포스트모템/체인지로그 분리 관행과 일치.
- 출처: [sre.google/sre-book/postmortem-culture](https://sre.google/sre-book/postmortem-culture/), [AWS Well-Architected — Runbooks](https://docs.aws.amazon.com/wellarchitected/2025-02-25/framework/ops_ready_to_support_use_runbooks.html)
- **반영**: [_template-troubleshooting.md](../08-troubleshooting/00-development-issues/_template-troubleshooting.md)에 담당자/마감일 필드, [08-troubleshooting/README.md](../08-troubleshooting/README.md)에 blameless 원칙과 반복 이슈 승격 규칙 추가.

## 조사 9 — AI 에이전트 컨텍스트 엔지니어링

- **핵심 발견**: Anthropic의 "context engineering" 원칙(최소·고신호 토큰), Chroma의 "context rot" 연구(컨텍스트가 길어질수록 노이즈로 인해 정확도가 저하되며 5만 토큰대에서도 이미 시작됨), JIT 검색(파일시스템 인덱스 + 필요시 로드)이 [doc-governance-policy.md](doc-governance-policy.md)의 덮어쓰기/append-only 분리·번호 폴더·컨트롤타워 우선 읽기와 원리적으로 동일하다. "Compaction Cliff" 연구는 계층적 요약이 안전 제약을 유실시킬 수 있음을 경고한다.
- 출처: [anthropic.com/engineering/effective-context-engineering-for-ai-agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents), [trychroma.com/research/context-rot](https://www.trychroma.com/research/context-rot), [anthropic.com/engineering/effective-harnesses-for-long-running-agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents)
- **반영**: [doc-governance-policy.md](doc-governance-policy.md)에 외부 연구 인용으로 근거 보강, 압축/승격 시 07-decisions·검증기준은 요약 대상에서 제외하는 예외 조항 추가.

## 조사 10 — 경쟁 스펙 기반/에이전트 네이티브 스캐폴딩

- **핵심 발견**: spec-kit(★135k, constitution.md가 모든 산출물의 기준점), BMAD-METHOD(★52k, 작업 규모에 따라 계획 깊이를 조절하는 scale-adaptive 원칙)가 실제로 존재하며 인기가 높다. 이들이 공통으로 풀려는 문제는 "에이전트가 조용히 내린 결정을 어떻게 지속 가능한 컨텍스트로 고정하고 여러 도구가 재사용하게 만드는가" — SuperDocs는 결정 고정([07-decisions](../07-decisions/README.md), [11-audit](../11-audit/README.md))은 이미 풀고 있으나 규모별 계획 깊이 조절과 다중 에이전트 이식성은 약하다.
- 출처: [github.com/github/spec-kit](https://github.com/github/spec-kit), [github.com/bmad-code-org/BMAD-METHOD](https://github.com/bmad-code-org/BMAD-METHOD)
- **반영**: [mastery/01-docs-blueprint](../../mastery/01-docs-blueprint/README.md)의 "프로젝트 정체성 요약" 절이 이미 constitution.md 역할을 하고 있음을 확인·명시. glob 기반 조건부 로딩과 preset/override 계층은 "문서를 사람도 함께 읽는다"는 이 하네스의 철학과 상충해 기각.

## 종합: 이 조사가 바꾼 것

가장 중요한 확인은 **부정이 아니라 긍정**이다 — 10개 조사 중 다수(조사 1, 2 일부, 3, 4 대부분, 8 대부분, 9)가 기존 설계를 "업계/공식 관행과 이미 일치한다"고 확인해줬다. 즉 단일 사례에만 의존했던 최초 설계가 우연히 여러 독립적 표준과 수렴해 있었다는 뜻이며, 이는 원래의 우려("한 사례에 매몰되어 있을 수 있다")를 상당 부분 완화한다. 동시에 명확한 격차(C4 Context 레벨 부재, ADR 결정동인 부재, Diátaxis Explanation 편중, 루트 AGENTS.md 표준 미준수, RTM 연결고리 부재)도 발견되어 각 대상 문서에 반영했다.

이 조사 자체도 영구 진실이 아니다 — 업계 관행은 계속 바뀐다. 다음 정기 감사([11-audit](../11-audit/README.md)) 때 이 조사가 여전히 유효한지 재확인한다.
