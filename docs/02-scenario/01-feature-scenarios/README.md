# 01-feature-scenarios — 기능 시나리오

기능 단위로 "어떤 조건에서 어떤 동작을 해야 하는가"를 구조화한다. 이 문서들은 QA의 시나리오 검증([05-test/03-scenario-verification](../../05-test/03-scenario-verification/README.md)) 기준이 된다.

## 파일명 규칙

`feature-<슬러그>.md`

## 템플릿

[_template-feature-scenario.md](_template-feature-scenario.md)

## 작성 원칙

- Given-When-Then 형식으로 조건-동작-결과를 명확히 한다.
- 정상 경로뿐 아니라 예외/경계 조건도 명시한다 (검증팀이 이 문서를 기준으로 테스트 케이스를 만든다).
- 기능이 코드로 구현되면 해당 코드 위치를 [04-code/01-business-logic](../../04-code/01-business-logic/README.md)에서 이 문서로 역참조한다.
