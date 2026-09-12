# 02-scenario — 시나리오 가이드

구체화하려는 서비스를 파악하고 정리하며, 해당 서비스/기능/의도가 **어떤 시나리오로 동작하는지**를 구조화하는 폴더다. [mastery/00-initial-intake](../../mastery/00-initial-intake/README.md)의 최초 인터뷰와 [10-consulting](../10-consulting/README.md)의 지속적인 논의에서 나온 답변이 여기서 구체적 시나리오로 승격되고, [03-plan](../03-plan/README.md)에서 실행 계획이 되고, [04-code](../04-code/README.md)에서 실제 코드 구조와 매핑된다.

## 하위 구조

| 폴더 | 내용 |
|---|---|
| [00-service-overview](00-service-overview/README.md) | 서비스 전체 개요, 핵심 가치 제안, 상위 기능 지도 |
| [01-feature-scenarios](01-feature-scenarios/README.md) | 기능 단위 시나리오 (Given-When-Then 형태) |
| [02-user-flows](02-user-flows/README.md) | 사용자 여정/화면 흐름 |

## 이 폴더의 역할

- "무엇을 만들어야 하는가"에 대한 **살아있는 명세**다. 코드가 바뀌면 여기도 갱신한다.
- AI가 새 기능을 구현하기 전에 여기서 관련 시나리오를 먼저 찾는다 — 없으면 만든 뒤 구현한다.
- 시나리오와 실제 구현이 어긋나면 [08-troubleshooting](../08-troubleshooting/README.md)에 기록할 가치가 있는지 검토한다.
