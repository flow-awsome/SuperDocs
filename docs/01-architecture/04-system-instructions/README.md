# 04-system-instructions — 시스템 인스트럭션

AI 에이전트가 이 프로젝트에서 어떻게 행동해야 하는지에 대한 운영 규칙. [AGENTS.md](../../AGENTS.md)가 요약본이라면, 이 폴더는 상세본이다.

## 파일

- `agent-operating-rules.md` — 에이전트 행동 원칙, 문서 참조/갱신 규칙, 에스컬레이션 기준
- `skill-usage-policy.md` — caveman류 압축 스킬, 탐색 전용 에이전트(ponytail류) 등 토큰 최적화 도구를 언제/어떻게 쓰는지

## 이 폴더가 존재하는 이유

AI가 매 세션 새로 컨텍스트를 잡을 때, "어떻게 일해야 하는가"를 다시 추론하게 두지 않고 명시적으로 지정해 디루전과 비일관성을 줄인다.

이 폴더는 arc42/C4/4+1 같은 업계 아키텍처 표준 어디에도 대응 항목이 없는 SuperDocs 고유 확장이다 — AI 에이전트가 개발 주체로 참여한다는 이 하네스의 전제 때문에 필요해졌다. 근거: [00-control-tower/external-reference-survey.md](../../00-control-tower/external-reference-survey.md#아키텍처-문서화-표준).

## 절차가 길어지면 여기 두지 않는다

상시 로드되는 규칙 파일과, 호출 시에만 로드되는 절차(스킬)는 구분해야 한다 — 상시 로드 파일에 상세 절차가 쌓이면 매 세션 불필요한 토큰을 태운다. [05-test](../../05-test/README.md)의 8종 검증 체크리스트, [11-audit](../../11-audit/README.md)의 감사 렌즈별 상세 수행 절차처럼 "사실이 아니라 절차"인 내용은 이 폴더에 요약만 남기고, 실제 단계별 지시는 별도 스킬/체크리스트 문서로 분리해 필요할 때만 참조한다. 근거: [00-control-tower/external-reference-survey.md](../../00-control-tower/external-reference-survey.md#에이전트-하네스-공식-가이드라인).
