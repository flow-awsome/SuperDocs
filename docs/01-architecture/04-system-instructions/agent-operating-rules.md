# 에이전트 운영 규칙 (상세)

## 1. 문서 우선 원칙

- 작업 전: 관련 [02-scenario](../../02-scenario/README.md), [07-decisions](../../07-decisions/README.md)를 먼저 확인해 이미 결정된 사항을 재논의하지 않는다.
- 작업 후: 영향받은 문서를 갱신한다 (코드만 바꾸고 문서를 방치하지 않는다).

## 2. 불확실성 처리 원칙

- 비즈니스 의도가 애매하면: 추측하지 않는다 → [10-consulting](../../10-consulting/README.md)에 질문을 남기거나 사용자에게 직접 확인한다.
- 기술적 구현 방식만 애매하면: 합리적 기본값으로 진행하되 [07-decisions](../../07-decisions/README.md)에 근거를 남긴다.
- 이 둘을 구분하는 기준: "틀리면 사용자가 원치 않는 기능이 나오는가(비즈니스)" vs "틀려도 리팩터링으로 고칠 수 있는가(기술)".

## 3. 문서 갱신 라우팅 규칙

| 상황 | 목적지 |
|---|---|
| 계획이 바뀌었다 | [03-plan](../../03-plan/README.md) + [06-history/01-plan-changelog](../../06-history/01-plan-changelog/README.md) |
| 비즈니스 로직이 바뀌었다 | [04-code](../../04-code/README.md) + [06-history/00-business-logic-changelog](../../06-history/00-business-logic-changelog/README.md) |
| 왜 그렇게 했는지 판단이 필요했다 | [07-decisions](../../07-decisions/README.md) |
| 문제를 겪고 해결했다 | [08-troubleshooting](../../08-troubleshooting/README.md) |
| 사용자가 해야 할 일이 생겼다 | [09-todo/00-manual-setup-tasks](../../09-todo/00-manual-setup-tasks/README.md) |
| 검증을 수행했다 | [05-test](../../05-test/README.md) |
| 다른 Git 저장소와의 경계에 걸친 작업이다 (공유 계약 변경, 인증 방식 변경 등) | [01-architecture/01-system-composition/related-repositories.md](../01-system-composition/related-repositories.md) (해당 파일이 있는 프로젝트만) |

## 4. 보고 원칙 (토큰 최적화)

- 진행 중 의미 없는 중간보고를 생략한다. "지금 무엇을 확인 중"이라는 서술 대신 결과가 나오면 결과와 다음 행동만 전달한다.
- 상세 근거/과정은 대화가 아니라 문서(결정기록, 히스토리)에 남기고 대화에서는 링크나 한 줄 요약으로 대체한다.
- 문서 자체도 중복을 피한다 — 같은 내용을 여러 폴더에 반복해서 쓰지 않고, 원본 하나를 두고 나머지는 링크한다.

## 5. 비판적 검토 의무

- 이 하네스의 어떤 문서도 맹목적으로 따르지 않는다. 문서가 현재 상황과 맞지 않으면 문제를 제기한다.
- 문서를 따르지 않기로 했다면 그 판단과 이유를 [07-decisions](../../07-decisions/README.md)에 남긴다 (판단 자체를 숨기지 않는다).

## 6. 완결성 vs 비용/속도 트레이드오프 판단 기준

- 매 결정에서 "지금 이 완결성이 실제로 이번 페이즈의 성공 기준에 기여하는가"를 먼저 묻는다 ([mastery/00-initial-intake/04-success-criteria-and-constraints.md](../../../mastery/00-initial-intake/04-success-criteria-and-constraints.md) 참조).
- 과설계가 의심되면 [10-consulting/02-decision-interviews](../../10-consulting/02-decision-interviews/README.md)를 통해 사용자와 확인한다.

## 7. 위험도 등급(Lv)과 사전 확인 게이트

작업 하나를 시작하기 전, 되돌리기 어려움과 영향 범위를 기준으로 위험도를 1~9로 어림잡는다 ([03-plan/01-steps](../../03-plan/01-steps/README.md)의 스텝 템플릿에 기록).

| 등급 | 예시 | 요구되는 인간 개입 |
|---|---|---|
| Lv 1-3 | 단순 CRUD 추가, 문서 오타 수정 | 없음 — 진행 후 결과만 보고 |
| Lv 4-5 | 새 모듈 추가, 화면 신설 | 완료 후 [05-test](../../05-test/README.md) 검증 필수 |
| Lv 6-7 | 인증/인가 변경, 스키마 변경, 외부 서비스 연동 | **착수 전** 사용자 확인 필수 ([10-consulting/02-decision-interviews](../../10-consulting/02-decision-interviews/README.md)) |
| Lv 8-9 | 테넌트 격리/권한 경계 변경, 프로덕션 데이터에 영향 | 착수 전 확인 + **모킹 없이 실제 DB/컨테이너로 실행한 증거 필수** + [05-test/02-integration-verification/regression-recheck-checklist.md](../../05-test/02-integration-verification/regression-recheck-checklist.md) 전체 재실행 + 완료 후 다음 [11-audit](../../11-audit/README.md) 라운드에서 재검증 전까지 "완료"로 간주하지 않음 |

이 등급표는 예시다 — 실제 임계값은 [mastery/00-initial-intake/04-success-criteria-and-constraints.md](../../../mastery/00-initial-intake/04-success-criteria-and-constraints.md)의 리스크 허용도에 맞게 [07-decisions](../../07-decisions/README.md)에 프로젝트별로 확정한다.

Lv6 이상 결정은 [07-decisions](../../07-decisions/README.md)의 ADR에도 위험도(Lv) 필드를 남겨, 나중에 "이 등급의 결정이 실제로 전부 ADR로 기록됐는지" 역추적할 수 있게 한다.

## 8. 관련 저장소(멀티레포) 조사 원칙

[01-architecture/01-system-composition/related-repositories.md](../01-system-composition/related-repositories.md)가 존재하는 프로젝트에만 적용된다.

- **평소에는 다른 저장소를 조회하지 않는다.** 경계에 걸친 작업(공유 계약 변경, 인증 방식 변경, 다른 저장소가 소비하는 인터페이스 추가/제거)이 실제로 생겼을 때만 레지스트리에서 해당 저장소를 찾아 "조사 시 우선 참조 문서" 링크만 확인한다 — 매 세션 선제적으로 관련 저장소를 전부 읽는 것은 이 하네스의 토큰 최적화 원칙에 위배된다.
- **접근 방법에 따라 조사 수단을 고른다**: public 저장소는 `WebFetch`로 raw 파일을 직접 읽고, 같은 조직의 private 저장소는 `gh api`로 조회하며, 접근 불가한 저장소는 추측하지 않고 사용자에게 현재 값을 확인하거나 [00-control-tower/open-questions.md](../../00-control-tower/open-questions.md)에 등록한다.
- **이 저장소의 결정이 다른 저장소에 영향을 준다면**, ADR 작성만으로는 전파되지 않는다 — `related-repositories.md`의 "최근 결정" 표에도 반드시 한 줄을 추가한다.
- **다른 저장소의 최근 결정이 이 저장소에 영향을 준 것을 확인했다면**, 대응 조치를 이 저장소의 [06-history](../../06-history/README.md)에 남기고 출처(다른 저장소의 ADR 링크)를 명시한다.

### 응답 가능한 인간이 없을 때의 기본 동작

Lv6 이상 게이트에 도달했는데 확인해줄 사람이 즉시 응답하지 않는 경우, AI는 추측으로 진행하지 않는다. 기본 동작은 **보수적으로 멈추고 대기**한다: 해당 작업을 [00-control-tower/open-questions.md](../../00-control-tower/open-questions.md)에 급함 표시와 함께 등록하고, 확인이 필요 없는 다른 작업으로 전환한다. "일단 진행하고 나중에 승인받는다"를 기본값으로 삼지 않는다 — 완전 무인 자율 운영을 의도적으로 허용하기로 했다면 그 결정 자체를 [07-decisions](../../07-decisions/README.md)에 ADR로 남기고 이 절을 프로젝트별로 갱신한다.
