# AGENTS.md — 프로젝트 스펙시트 & 에이전트 운영 규칙

이 파일은 새 AI 세션이 이 프로젝트에 처음 투입될 때 가장 먼저 읽는 문서다. "이 프로젝트가 무엇인지", "AI가 어떻게 행동해야 하는지"를 한 화면 분량으로 압축해 전달하는 것이 목적이다. 세부 내용은 각 하위 문서로 링크하고, 여기서는 뼈대만 유지한다 (토큰 최적화 원칙). 지금 이 순간의 상태는 [00-control-tower/project-dashboard.md](00-control-tower/project-dashboard.md)가 더 정확하다 — 이 파일은 잘 바뀌지 않는 정체성/규칙, 대시보드는 매일 바뀌는 상태.

> **가지치기 기준**: 이 파일에 줄을 추가하기 전에 "이 줄을 지우면 AI가 실수할까?"로 판정한다. 코드를 보면 유추 가능한 내용, 자주 바뀌는 정보는 여기 두지 않는다 (근거: [00-control-tower/external-reference-survey.md](00-control-tower/external-reference-survey.md#에이전트-하네스-공식-가이드라인)).
>
> **이 파일을 AI 도구가 자동으로 찾게 하려면**: 업계 표준은 저장소 **루트**의 `AGENTS.md`(또는 `CLAUDE.md`가 `@AGENTS.md`를 import)다. 이 저장소를 실제 프로젝트에 적용했다면 루트에 얇은 `AGENTS.md`를 두고 이 파일(`docs/AGENTS.md`)로 링크하는 것을 권장한다 (근거: [00-control-tower/external-reference-survey.md](00-control-tower/external-reference-survey.md#ai-코딩-도구의-프로젝트-컨텍스트-관례)).

## 1. 프로젝트 정체성 (요약)

> 이 섹션은 [../mastery/00-initial-intake/01-project-questionnaire.md](../mastery/00-initial-intake/01-project-questionnaire.md) 완료 후 채운다.

- **서비스 한 줄 정의**: (미작성)
- **핵심 사용자**: (미작성)
- **핵심 성공 기준**: (미작성)
- **현재 페이즈**: (미작성) → [03-plan/00-phases](03-plan/00-phases/README.md) 참조

## 2. 기술 스택 (이 프로젝트 확정값)

[../mastery/00-initial-intake/02-tech-stack-baseline.md](../mastery/00-initial-intake/02-tech-stack-baseline.md)에서 시나리오에 맞게 확정한 내용을 채운다 — 이 하네스는 특정 언어·프레임워크를 전제하지 않는다.

| 영역 | 확정값 | 비고 |
|---|---|---|
| 언어 | (미작성) | 서비스 특성에 따라 영역별로 분리 배정 가능 |
| 백엔드 프레임워크 | (미작성) | 모듈 경계는 [01-architecture/01-system-composition](01-architecture/01-system-composition/README.md) 참조 |
| 프론트엔드 프레임워크 | (미작성) | 백엔드 API 호출 방식 확정 |
| DB | (미작성) | 스키마 변경은 반드시 [06-history/00-business-logic-changelog](06-history/00-business-logic-changelog/README.md)에 기록 |
| 캐시/큐 | (미작성) | 세션, 캐시, 비동기 큐 용도 분리 명시 |
| 인프라 | (미작성) | 완결성과 비용 산정을 항상 함께 검토 — [../mastery/00-initial-intake/02-tech-stack-baseline.md](../mastery/00-initial-intake/02-tech-stack-baseline.md)의 비용 섹션 참조 |
| CI/CD | (프로젝트별 확정 필요) | 유지보수 지속가능성 관점에서 설계 |

## 3. 에이전트 운영 규칙 (핵심)

전체 규칙은 [01-architecture/04-system-instructions/agent-operating-rules.md](01-architecture/04-system-instructions/agent-operating-rules.md)에 있다. 여기서는 최우선 원칙만 요약한다.

1. **문서를 먼저 찾고, 없으면 만든다.** 같은 결정을 두 번 논의하지 않는다 — [07-decisions](07-decisions/README.md)를 먼저 검색한다.
2. **작업 단위마다 기록 위치가 다르다.**
   - 계획 변경 → [03-plan](03-plan/README.md)
   - 코드 구조/로직 파악 → [04-code](04-code/README.md)
   - 검증 결과 → [05-test](05-test/README.md)
   - 있었던 일(사실) → [06-history](06-history/README.md)
   - 왜 그렇게 하기로 했는지(판단) → [07-decisions](07-decisions/README.md)
   - 겪은 문제와 해결 → [08-troubleshooting](08-troubleshooting/README.md)
   - 사용자가 해야 할 일 / 사용자에게 물어볼 일 → [09-todo](09-todo/README.md)
   - 지속적인 방향 논의/질의응답 → [10-consulting](10-consulting/README.md)
   - 정기 전수조사/교차검증 결과 → [11-audit](11-audit/README.md)
3. **불확실하면 추측해서 진행하지 않고 [10-consulting](10-consulting/README.md)에 질문을 남기거나 사용자에게 직접 확인한다.** 특히 비즈니스 로직의 의도가 애매할 때. 확인이 필요한 항목이 쌓이면 [00-control-tower/open-questions.md](00-control-tower/open-questions.md)에도 등록한다.
4. **진행 중 의미없는 중간보고를 하지 않는다.** 결과와 다음 행동만 전달한다. 상세 근거가 필요하면 문서에 기록하고 링크로 대체한다.
5. **토큰 최적화 스킬 사용 정책**은 [skill-usage-policy.md](01-architecture/04-system-instructions/skill-usage-policy.md) 참조 (caveman류 압축 모드, 탐색 전용 에이전트 등을 언제 쓰는지).
6. **문서는 규칙이 아니라 참고자료다.** 상황에 맞지 않으면 비판적으로 문제를 제기하되, 무시하기로 했다면 그 판단을 [07-decisions](07-decisions/README.md)에 남긴다.
7. **문서를 새로 쓰거나 갱신할 때는 [00-control-tower/doc-governance-policy.md](00-control-tower/doc-governance-policy.md)의 해당 폴더 규칙(덮어쓰기/append-only, 크기 예산)을 따른다.** 특히 상태성 문서에 로그를 계속 append하지 않는다 — 이것이 실제 프로젝트에서 문서를 사람이 검토 불가능하게 만든 가장 흔한 원인이다.

## 4. 새 세션 부트스트랩 체크리스트

새 AI 세션이 이 프로젝트에 투입되면 다음 순서로 컨텍스트를 잡는다:

1. [00-control-tower/project-dashboard.md](00-control-tower/project-dashboard.md) — 지금 상태
2. 이 파일(`AGENTS.md`) 전체 확인
3. 작업 요청과 관련된 `02-scenario/` 문서 확인 (해당 기능이 이미 정의되어 있는지)
4. 작업 요청과 관련된 `03-plan/00-phases/` 현재 페이즈 확인
5. 관련 `07-decisions/`에 과거 결정이 있는지 검색
6. 작업 완료 후 영향받는 `06-history`, `07-decisions`, `09-todo`, `00-control-tower/project-dashboard.md` 갱신 여부 판단

## 5. 문서 오너십 매핑 (참고용 — 인력 규모와 무관하게 적용)

아래 표는 "팀이 10개 있어야 한다"는 뜻이 아니다. AI 혼자 개발을 진행하는 프로젝트라면 한 명(또는 AI 하나)이 이 모든 행의 역할을 순서대로 겸한다 — 역할이 사라지는 게 아니라 한 사람에게 합쳐질 뿐이다. 인력이 늘면 아래처럼 역할별로 나눠 맡을 수 있다는 예시로만 참고한다:

| 역할 | 주 오너십 폴더 |
|---|---|
| 아키텍처 | 01-architecture |
| 프로덕트/기획 | 10-consulting, 02-scenario |
| 백엔드 (도메인 A) | 04-code (해당 모듈), 03-plan |
| 백엔드 (도메인 B, 있는 경우) | 04-code (해당 모듈), 03-plan |
| 프론트엔드 | 04-code (해당 모듈), 02-scenario/02-user-flows, 05-test/04-ui-verification |
| QA/검증 | 05-test |
| 인프라/SRE | 01-architecture/00-system-foundation, 08-troubleshooting |
| 데이터/DB | 04-code, 06-history/00-business-logic-changelog |
| PMO/진행관리 | 03-plan, 06-history, 09-todo, 00-control-tower |
| 의사결정/거버넌스 | 07-decisions |
| 감사/품질보증 | 11-audit |

이 매핑은 강제가 아니라 책임 소재를 빠르게 찾기 위한 참고표다. [11-audit/00-audit-charters](11-audit/00-audit-charters/README.md)의 감사 렌즈도 마찬가지로 인원 수만큼만 쓴다 — 1인/1개 AI라면 관점을 바꿔가며 순서대로 렌즈를 적용해 같은 교차검증 효과를 낸다.
