# 01-architecture — 아키텍처

시스템이 "무엇으로, 어떻게, 왜 그렇게" 구성되어 있는지를 담는다. 코드의 실제 흐름은 [04-code](../04-code/README.md)에, 시스템이 어떤 시나리오로 동작해야 하는지는 [02-scenario](../02-scenario/README.md)에 있다 — 이 폴더는 그 둘을 잇는 **구조적 뼈대**다.

## 하위 구조

| 폴더 | 질문 | 내용 |
|---|---|---|
| [00-system-foundation](00-system-foundation/README.md) | 무엇으로 만드는가 | 기술 스택, 컨벤션, 환경/인프라 베이스라인 |
| [01-system-composition](01-system-composition/README.md) | 어떻게 나뉘는가 | 모듈/서비스 경계, 컴포넌트 지도 |
| [02-system-logic](02-system-logic/README.md) | 어떻게 동작하는가 | 핵심 도메인 로직, 데이터 흐름 |
| [03-system-definition](03-system-definition/README.md) | 무엇이 아닌가 | 용어집, 도메인 모델 정의, 비목표/경계 |
| [04-system-instructions](04-system-instructions/README.md) | AI는 어떻게 행동하는가 | 에이전트 운영 규칙, 스킬 사용 정책 |

## 갱신 원칙

- 이 폴더는 **현재 상태(is)**를 담는다. "왜 이렇게 결정했는가"는 [07-decisions](../07-decisions/README.md), "어떻게 바뀌어왔는가"는 [06-history](../06-history/README.md)에 있다.
- 아키텍처 변경이 확정되면: (1) 이 폴더의 문서를 최신 상태로 갱신 → (2) [06-history/00-business-logic-changelog](../06-history/00-business-logic-changelog/README.md) 또는 관련 히스토리에 변경 기록 → (3) 근거는 [07-decisions](../07-decisions/README.md)에 남긴다.
- 코드와 문서가 어긋나면 코드를 진실로 간주하고 문서를 갱신한다. 어긋남을 발견하면 [08-troubleshooting](../08-troubleshooting/README.md)에 기록할 가치가 있는지도 검토한다.
