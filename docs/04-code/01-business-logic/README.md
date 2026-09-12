# 01-business-logic — 비즈니스 로직 맵

[02-scenario/01-feature-scenarios](../../02-scenario/01-feature-scenarios/README.md)의 각 시나리오가 실제로 어느 파일/함수에 구현되어 있는지를 역참조 가능하게 기록한다.

## 템플릿

[_template-business-logic-scenario-map.md](_template-business-logic-scenario-map.md)

## 작성 원칙

- 코드를 다시 설명하지 않는다 (코드 자체가 설명이다). 대신 "이 시나리오 → 이 파일의 이 함수"라는 **위치 인덱스** 역할만 한다.
- 로직이 복잡해 코드만으로 의도 파악이 어려운 경우에만 왜 그렇게 구현했는지 한두 줄 보충하고, 상세 근거는 [07-decisions/00-logic-decisions](../../07-decisions/00-logic-decisions/README.md)로 링크한다.
