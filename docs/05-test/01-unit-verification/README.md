# 01-unit-verification — 단위 검증

함수/클래스 단위의 격리된 테스트. 외부 의존성(DB, 네트워크)은 모킹한다.

## 도구

| 대상 | 도구 |
|---|---|
| 백엔드 (도메인 A) | (확정 필요) |
| 백엔드 (도메인 B, 있는 경우) | (확정 필요) |
| 프론트엔드 | (확정 필요) |

## 커버리지 기준

- 핵심 비즈니스 로직([04-code/01-business-logic](../../04-code/01-business-logic/README.md)): 목표 커버리지 (%)
- 단순 CRUD/DTO: 낮은 우선순위

## 작성 원칙

- 하나의 단위 테스트는 하나의 행동만 검증한다.
- [02-scenario/01-feature-scenarios](../../02-scenario/01-feature-scenarios/README.md)의 Given-When-Then을 테스트 케이스명에 반영한다.
