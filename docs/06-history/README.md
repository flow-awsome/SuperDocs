# 06-history — 히스토리

**있었던 일**을 시간순으로 기록한다. "왜 그렇게 했는가"의 판단 근거는 [07-decisions](../07-decisions/README.md)에 별도로 있다 — 히스토리는 사실(fact), 결정기록은 판단(judgment)이다.

## 하위 구조

| 폴더 | 내용 |
|---|---|
| [00-business-logic-changelog](00-business-logic-changelog/README.md) | 비즈니스 로직/API 계약 변경 이력 |
| [01-plan-changelog](01-plan-changelog/README.md) | 계획(페이즈/스텝) 변경 이력 |
| [02-progress-log](02-progress-log/README.md) | 전반적 진행상황 로그 |
| [03-phase-progress-log](03-phase-progress-log/README.md) | 페이즈별 진행률/마일스톤 로그 |

## 작성 원칙

- 히스토리는 **추가만 한다** (append-only). 과거 기록을 지우거나 고쳐쓰지 않는다 — 잘못된 판단이었더라도 그 자체가 기록 가치가 있다.
- 최신 상태 요약이 필요하면 [01-architecture](../01-architecture/README.md)나 [03-plan](../03-plan/README.md)를 갱신하고, 여기는 "언제 무엇이 바뀌었는지"의 타임라인 역할만 한다.
