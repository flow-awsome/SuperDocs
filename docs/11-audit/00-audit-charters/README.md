# 00-audit-charters — 감사 렌즈 정의

감사 라운드마다 "누가(어떤 렌즈로) 무엇을 본다"를 먼저 정의한다. 정의 없이 감사를 시작하면 감사자마다 제각각의 기준으로 훑게 되어 결과를 교차 대조할 수 없다.

## 참고 렌즈 세트 (최대 10개 — 가용 인력/시간에 맞게 고른다)

아래는 상한선 참고 목록이지 필수 개수가 아니다. 1인 프로젝트나 AI 혼자 진행하는 프로젝트라면 이번 라운드에 가장 리스크가 큰 2~3개만 골라 적용해도 충분하고, 시간이 나면 나머지를 순서대로 이어서 적용한다 — 핵심은 렌즈 개수가 아니라 **매번 처음부터 다른 관점으로 다시 보는 것**이다.

| # | 렌즈 | 보는 것 | 근거 문서 |
|---|---|---|---|
| 1 | 아키텍처 정합성 | 설계([01-architecture](../../01-architecture/README.md))와 실제 구현이 일치하는가 | |
| 2 | 보안 | 인증/인가, 데이터 보호, 입력 검증 취약점 | [05-test/05-nonfunctional-verification](../../05-test/05-nonfunctional-verification/README.md) |
| 3 | 인프라/비용 준비도 | 인프라 구성이 실제 트래픽/예산에 맞는가, 과설계/과소설계 여부 | [01-architecture/00-system-foundation/environment-and-infra-baseline.md](../../01-architecture/00-system-foundation/environment-and-infra-baseline.md) |
| 4 | 테스트 무결성 | 테스트가 실제로 의미 있는 것을 검증하는가 (모킹 남용, 그린이지만 공허한 테스트) | [05-test](../../05-test/README.md) |
| 5 | 문서-코드 정합성 | 문서가 설명하는 것과 코드가 실제로 하는 것이 일치하는가 | [04-code](../../04-code/README.md) |
| 6 | 비즈니스 로직 전수 | 도메인 규칙이 시나리오대로 전부 구현/처리되는가, 누락된 예외 케이스 | [02-scenario/01-feature-scenarios](../../02-scenario/01-feature-scenarios/README.md) |
| 7 | API 계약 커버리지 | 대외 계약(OpenAPI 등)이 실제 엔드포인트를 빠짐없이 반영하는가 | [04-code/02-api-contracts](../../04-code/02-api-contracts/README.md) |
| 8 | 모듈 경계 위반 | 순환 의존, 계층 침범, 소유권 위반 | [01-architecture/01-system-composition](../../01-architecture/01-system-composition/README.md) |
| 9 | 기획의도 정합성 | 원래 의도한 기획([02-scenario](../../02-scenario/README.md))과 실제 구현/최근 변경 사이의 괴리 | [06-history](../../06-history/README.md) |
| 10 | 문서 위생/최신성 | 문서 비대화, 중복, 최신성 — [doc-governance-policy.md](../../00-control-tower/doc-governance-policy.md) 준수 여부 | [00-control-tower](../../00-control-tower/README.md) |

## 템플릿

[_template-audit-charter.md](_template-audit-charter.md) — 감사 라운드마다 이 템플릿으로 실제 적용할 렌즈 조합과 각 렌즈의 구체적 체크리스트를 정의한다.

## 작성 원칙

- 렌즈는 매번 똑같이 반복하지 않는다 — 직전 라운드에서 문제가 많이 나온 영역, 최근 크게 변경된 영역에 렌즈를 추가하거나 강화한다.
- 렌즈 하나는 반드시 "무엇을 근거로 판정하는가"가 명시되어야 한다 (감정적 판단 금지, 파일/문서 근거 필수).
