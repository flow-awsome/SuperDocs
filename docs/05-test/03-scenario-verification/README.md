# 03-scenario-verification — 시나리오 검증

[02-scenario/01-feature-scenarios](../../02-scenario/01-feature-scenarios/README.md)에 정의된 시나리오가 실제로 end-to-end로 동작하는지 검증한다.

## 도구

- E2E: Playwright / Cypress (Next.js 포함 전체 흐름)
- API E2E: supertest 등

## 작성 원칙

- 시나리오 문서의 Given-When-Then을 그대로 테스트 스텝으로 옮긴다.
- 시나리오 문서와 테스트 파일을 상호 링크한다 (시나리오 문서 하단 "검증 링크" 섹션).
- 시나리오가 바뀌면 이 검증도 함께 갱신한다 — 갱신 누락은 [08-troubleshooting](../../08-troubleshooting/README.md)에 반복되면 기록.
