# 문서 거버넌스 정책

`docs/` 전체가 프로젝트 기간 내내 무한정 커지는 것을 막기 위한 폴더별 규칙. 새 폴더/문서 유형을 추가할 때는 이 표에 먼저 등록한다.

## 폴더별 변경 정책

| 폴더 | 변경 방식 | 크기/개수 예산 | 오너 | 검토 주기 |
|---|---|---|---|---|
| [00-control-tower](README.md) | project-dashboard/open-questions는 **덮어쓰기 전용**, governance-policy는 정책 변경 시만 | dashboard ≤150줄, open-questions ≤20건 | PMO | 매 페이즈 |
| [01-architecture](../01-architecture/README.md) | **현재 상태로 덮어쓰기** (로그 아님) | 문서당 ≤300줄, 넘으면 하위 분할 | 아키텍처 리드 | 6~12개월 또는 구조 변경 시 |
| [02-scenario](../02-scenario/README.md) | 현재 상태로 덮어쓰기, 상태 필드(초안/확정/구현완료)로 이력 표시 | 기능당 1파일 | 프로덕트 리드 | 매 페이즈 |
| [03-plan](../03-plan/README.md) | phases/steps는 덮어쓰기(계획), step-logs는 append-only | step-log 파일당 ≤200줄 | PMO | 매 스텝 |
| [04-code](../04-code/README.md) | 현재 상태로 덮어쓰기 (코드가 진실, 문서는 지도) | | 각 모듈 오너 | 리팩터링 시마다 |
| [05-test](../05-test/README.md) | 검증 기준은 덮어쓰기, 결과 자체는 CI가 진실 | | QA 리드 | 매 페이즈 |
| [06-history](../06-history/README.md) | **append-only, 절대 수정 금지** | 하위 폴더당 월 20파일 초과 시 `archive/YYYY-MM/`로 이동 + 인덱스 파일 작성 | PMO | 월 1회 정리(내용 검토 아님, 정리만) |
| [07-decisions](../07-decisions/README.md) | **append-only, 절대 수정 금지.** 뒤집힌 결정은 새 ADR + superseded 표시 | ADR 1건 = 결정 1개 (여러 결정 묶지 않음) | 결정권자 | 재검토 조건 도달 시 |
| [08-troubleshooting](../08-troubleshooting/README.md) | append-only, 해결 후에도 삭제 안 함 | | 발견자 | 반기 1회 (여전히 유효한지) |
| [09-todo](../09-todo/README.md) | 진행중 항목은 상태 갱신(덮어쓰기), 완료 항목은 삭제 안 하고 상태만 "완료" | 열려있는 항목 ≤30건 | PMO | 주간 |
| [10-consulting](../10-consulting/README.md) | phase-consulting/decision-interviews는 세션당 1파일, discussion-log만 주제별 누적 허용 | discussion-log 주제당 ≤300줄, 넘으면 결론만 남기고 나머지는 승격 처리 | 세션 진행자 | 각 세션 종료 시 |
| [11-audit](../11-audit/README.md) | 리포트는 append-only, 차터는 덮어쓰기 | | 감사 라운드 진행자 | 페이즈 종료/배포 전 |

> **오너 컬럼은 인력 수만큼만 채운다.** 1인 프로젝트나 AI 단독 운영이면 위 표의 모든 행을 "본인" 한 명이 겸한다 — 인력이 부족해서 못 지키는 규칙이 아니라, 애초에 "누가 봐도 매 순간 최신 상태인지 확인할 책임이 있다"는 뜻만 담은 컬럼이다.

## 05-test 세부 예산 (보강)

- 검증 기준 문서: 문서당 ≤300줄 (01-architecture와 동일 기준)
- [07-manual-verification-checklist](../05-test/07-manual-verification-checklist/README.md)의 체크리스트 파일: 파일당 ≤100줄, 넘으면 배포 전/페이즈 종료 등 시점별로 분할
- [08-verification-setup](../05-test/08-verification-setup/README.md): 목차만 있고 실행 커맨드가 비어있는 상태를 "완료"로 간주하지 않는다 — 최소 1회는 실제로 그 커맨드를 실행해 확인한 내용이어야 한다

## 크기·개수 예산을 지키는 방법

- **덮어쓰기 문서가 예산을 넘으려 할 때**: 하위 항목으로 분할하거나(예: `01-architecture`의 파일이 커지면 세부 파일로 쪼갠다), 오래된 내용을 [06-history](../06-history/README.md)로 이관한다.
- **append-only 문서가 개수 예산을 넘으려 할 때**: 삭제하지 않고 `archive/YYYY-MM/` 하위 폴더로 이동한 뒤, 그 폴더에 요약 인덱스(`archive/YYYY-MM/README.md`, 각 파일 한 줄 요약)를 만든다. 원본은 그대로 보존한다 (git 이력만 믿지 않는다 — 이 하네스는 git 없는 환경에서도 쓰일 수 있다).
- **버전 전체를 스냅샷으로 얼리는 방식(예: `v0/`, `v1/` 전체 디렉토리 복제)은 지양한다.** 특정 시점의 전체 트리를 통째로 얼리면 문서량이 배로 늘고, "지금 뭘 봐야 하는지"가 다시 헷갈리게 된다. 대신 개별 문서 단위로만 보관하고, 상위 구조가 바뀌는 결정은 [07-decisions](../07-decisions/README.md)의 ADR로 남긴다.

## 오너십 원칙

- 문서는 **팀 단위가 아니라 문서 단위로** 오너를 지정한다. 오너가 불분명한 문서가 가장 먼저 방치된다.
- 오너는 검토 주기가 돌아오면 "이 문서가 여전히 맞는지" 확인하고 상태를 갱신할 책임이 있다 — 새로 쓸 필요는 없고, "확인함 (YYYY-MM-DD)" 한 줄이면 충분하다.

## 문서 최신성 표시 (권장 헤더)

살아있는 문서(01-architecture, 02-scenario, 04-code 등)에는 파일 상단에 다음을 남기는 것을 권장한다:

```
> 오너: (이름/역할) · 마지막 확인: (YYYY-MM-DD) · 상태: 현재 / 검토필요 / 대체됨
```

정기 점검 시 이 헤더만 훑으면 어떤 문서가 오래됐는지 사람이 빠르게 판단할 수 있다.

## 규모가 작은 프로젝트/1인 운영을 위한 축소 경로

이 하네스의 3단 계층([03-plan](../03-plan/README.md)의 phase→step→step-log 등)은 페이즈가 많고 인력이 여러 명일 때를 기준으로 설계됐다. 페이즈가 1~2개뿐인 소규모 프로젝트나 1인/AI 단독 운영에서는 다음처럼 축소해도 된다 — 이것도 원칙 위반이 아니라 정식으로 허용된 경로다:

- `03-plan/02-step-logs`를 생략하고, 진행 기록을 해당 `03-plan/01-steps`의 스텝 문서에 직접 짧게 남긴다.
- `10-consulting/01-phase-consulting`의 첫 킥오프 세션은 [mastery/00-initial-intake](../../mastery/00-initial-intake/README.md) 인터뷰로 대체하고 별도로 다시 진행하지 않는다 (스코프가 그 사이 크게 안 바뀌었다면).
- [11-audit](../11-audit/README.md)의 렌즈는 10개 중 리스크가 큰 2~3개만 순환 적용한다.

축소했다는 사실 자체는 기록하지 않아도 된다 — 이 경로를 쓴다는 것 자체가 이미 이 정책이 허용한 정상 운영이다.

## 사람이 "문서가 너무 방대해졌다"고 느낄 때의 대응 순서

1. [00-control-tower/project-dashboard.md](project-dashboard.md)만 먼저 읽는다 — 그것으로 충분하면 나머지는 안 읽어도 된다.
2. 특정 폴더가 유독 방대하면 이 표에서 그 폴더의 예산을 확인하고, 초과했다면 위 "크기·개수 예산을 지키는 방법"에 따라 정리한다.
3. 정리 자체도 하나의 작업이다 — [03-plan](../03-plan/README.md)에 "문서 정리" 스텝으로 등록하고 진행한다 (방치하지 않는다).
