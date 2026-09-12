# 05-test — 테스트/검증

정적 검증부터 수동 검증까지, 검증 유형별로 폴더를 분리한다. 각 검증 유형은 검증 대상, 도구, 통과 기준이 다르므로 하나로 뭉치지 않는다.

## 하위 구조

| 폴더 | 검증 유형 | 대상 |
|---|---|---|
| [00-static-verification](00-static-verification/README.md) | 정적 검증 | 린트, 타입체크, 정적분석 |
| [01-unit-verification](01-unit-verification/README.md) | 단위 검증 | 함수/클래스 단위 |
| [02-integration-verification](02-integration-verification/README.md) | 통합 검증 | 모듈 간, DB/Redis 연동 |
| [03-scenario-verification](03-scenario-verification/README.md) | 시나리오 검증 | [02-scenario](../02-scenario/README.md) 기반 E2E |
| [04-ui-verification](04-ui-verification/README.md) | UI 검증 | Next.js 화면, 접근성, 반응형 |
| [05-nonfunctional-verification](05-nonfunctional-verification/README.md) | 비기능 검증 | 성능, 보안, 가용성 |
| [06-environment-verification](06-environment-verification/README.md) | 현장 환경 검증 | staging/production 실환경 |
| [07-manual-verification-checklist](07-manual-verification-checklist/README.md) | 수동 검증 체크리스트 | 자동화 안 된 항목 |
| [08-verification-setup](08-verification-setup/README.md) | 검증 세팅 방법 | 테스트 환경 구축 가이드 |

## 검증 결과 기록 원칙

- 검증 통과/실패 결과 자체는 CI 로그가 진실이다. 이 폴더는 "무엇을 어떻게 검증하는가"의 기준과, 반복적으로 문제가 되는 케이스를 남긴다.
- 검증 중 발견한 결함/트러블은 [08-troubleshooting](../08-troubleshooting/README.md)에 기록한다.
- 성공 기준의 근거는 [mastery/00-initial-intake/04-success-criteria-and-constraints.md](../../mastery/00-initial-intake/04-success-criteria-and-constraints.md)를 따른다.
