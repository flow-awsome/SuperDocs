# 마스터 독스 — (프로젝트명) 하네스 설정 계획

> 이 문서는 [00-initial-intake](../00-initial-intake/README.md) 인터뷰 완료 후 작성하는 최종 산출물이다. 이 프로젝트의 `docs/`를 실제로 어떻게 채울지에 대한 작업 지시서 역할을 한다. 완성되면 이 계획대로 `../../docs/`를 채우고, 이 파일 자체는 mastery에 남겨 "왜 이렇게 구성했는지"의 기록으로 보존한다.

- 작성일: (YYYY-MM-DD)
- 작성자:

## 1. 프로젝트 정체성 요약

(00-initial-intake/01-project-questionnaire.md에서 요약)

> 이 절은 spec-kit류 오픈소스 프로젝트가 쓰는 `constitution.md`(모든 후속 산출물의 기준점이 되는 단일 원칙 문서)와 같은 역할을 한다 — 별도 파일을 새로 만들지 않고 이미 이 위치가 그 기능을 하고 있음을 외부 조사로 확인했다. 근거: [docs/00-control-tower/external-reference-survey.md — 조사 10](../../docs/00-control-tower/external-reference-survey.md#조사-10--경쟁-스펙-기반에이전트-네이티브-스캐폴딩).

- 서비스 한 줄 정의:
- 핵심 사용자:
- 이번 페이즈 우선순위 (완결성 vs 속도, 비용 vs 성능):

## 2. 확정 기술 스택

(00-initial-intake/02-tech-stack-baseline.md에서 확정)

| 영역 | 확정값 | 하네스 기본값과의 편차 |
|---|---|---|
| 백엔드 | | |
| 프론트엔드 | | |
| DB/캐시 | | |
| 인프라 | | |

## 3. docs/ 모듈 구성 결정

| 모듈 | 사용 여부 | 사유 |
|---|---|---|
| 00-control-tower | 항상 사용 | |
| 01-architecture ~ 09-todo | 항상 사용 | |
| 10-consulting | 항상 사용 | |
| 11-audit | 항상 사용 (렌즈 수는 아래 4절) | |
| 12-customers (선택) | 사용 / 미사용 | 멀티고객사 여부에 따름 |

## 4. 감사 체계 설정

- 이번 프로젝트에서 실제로 운용할 감사 라운드 참여 인원/팀 수:
- 선택한 감사 렌즈 ([docs/11-audit/00-audit-charters](../../docs/11-audit/00-audit-charters/README.md)의 10개 중):
  1.
  2.
  3.
- 첫 감사 라운드 예정 시점:

## 5. 위험도(Lv) 임계값

| 항목 | 값 |
|---|---|
| 착수 전 사용자 확인 필수 최소 등급 | Lv (기본 6) |
| 완료 후 재검증 필수 최소 등급 | Lv (기본 8) |
| "되돌리기 어려움"의 이 프로젝트 기준 | |

## 6. 문서 거버넌스 예산 조정

[docs/00-control-tower/doc-governance-policy.md](../../docs/00-control-tower/doc-governance-policy.md)의 기본값에서 조정이 필요한 항목만 기록 (없으면 "기본값 그대로 사용"):

| 폴더 | 기본 예산 | 조정값 | 사유 |
|---|---|---|---|
| | | | |

## 7. 팀 매핑 (해당하는 경우)

[docs/AGENTS.md](../../docs/AGENTS.md) 5절 표를 이 프로젝트의 실제 팀 구성으로 갱신.

## 8. 생략하거나 변형한 항목

이 하네스의 기본 구조 중 이번 프로젝트에서 의도적으로 생략/변형한 것과 이유:

| 항목 | 처리 | 이유 |
|---|---|---|

## 9. 다음 행동

- [ ] `docs/AGENTS.md` 1~2절 채우기
- [ ] `docs/00-control-tower/project-dashboard.md` 초기값 채우기
- [ ] `docs/02-scenario/00-service-overview/service-overview.md` 채우기
- [ ] `docs/03-plan/00-phases/`에 첫 페이즈 등록
- [ ] (선택) `docs/12-customers/` 모듈 생성
- [ ] 팀에 "이제부터 `docs/`가 기준"이라고 공지
