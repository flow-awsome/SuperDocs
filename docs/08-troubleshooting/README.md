# 08-troubleshooting — 트러블 슈팅 가이드

개발 중, 시나리오 실행 중, 검증 과정 중 겪은 문제와 해결책을 카테고리별로 축적한다. **같은 문제를 두 번 처음부터 디버깅하지 않기 위한** 검색형 문서다.

## 하위 구조

| 폴더 | 내용 |
|---|---|
| [00-development-issues](00-development-issues/README.md) | 개발 중 도달한 트러블 (빌드, 의존성, 환경설정 등) |
| [01-scenario-issues](01-scenario-issues/README.md) | 특정 시나리오 구현/실행 중 겪은 트러블 |
| [02-verification-issues](02-verification-issues/README.md) | 사용자가 검증 과정에서 겪을 수 있는 트러블 대응 가이드 |

## 작성 원칙

- 형식 고정: 증상 → 원인 → 해결 → 재발 방지.
- 검색 가능하게 에러 메시지 원문을 그대로 포함한다 (요약하지 않는다 — 다음 사람이 검색으로 찾아야 한다).
- 근본 원인이 설계/코드 결함이면 [07-decisions](../07-decisions/README.md) 또는 [04-code](../04-code/README.md)에도 반영이 필요한지 판단한다.
- **Blameless 원칙**: 특정 사람/에이전트의 실수가 아니라 설계·프로세스의 gap으로 서술한다. "누가 실수했는가"가 아니라 "무엇이 이 실수를 가능하게 했는가"를 기록해야 재발을 막을 수 있다 (Google SRE 포스트모템 문화 근거: [00-control-tower/external-reference-survey.md — 조사 8](../00-control-tower/external-reference-survey.md#조사-8--인시던트트러블슈팅-지식-문화-sre)).
- **같은 유형의 이슈가 3회 이상 반복되면** 개별 트러블 기록에 계속 쌓아두지 말고 [07-decisions](../07-decisions/README.md)에 근본 원인 해결을 위한 ADR을 만들지 검토한다.
