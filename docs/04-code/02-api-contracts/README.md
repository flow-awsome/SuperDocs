# 02-api-contracts — API 계약

서비스 간(NestJS ↔ FastAPI), 프론트-백엔드 간(Next.js ↔ 백엔드) API 계약을 명세한다. OpenAPI/스키마 자동생성 도구가 있다면 그 산출물을 진실로 삼고, 이 폴더는 요약과 변경 이력 관점의 보충 문서로 유지한다.

## 파일명 규칙

`api-<서비스명>-<슬러그>.md`

## 템플릿

[_template-api-contract.md](_template-api-contract.md)

## Breaking Change 처리

계약이 하위 호환을 깨는 방식으로 바뀌면:
1. [07-decisions/01-architecture-decisions](../../07-decisions/01-architecture-decisions/README.md)에 근거 기록
2. [06-history/00-business-logic-changelog](../../06-history/00-business-logic-changelog/README.md)에 변경 이력 기록
3. 영향받는 소비자 서비스 팀에게 [09-todo/01-dev-communication-log](../../09-todo/01-dev-communication-log/README.md)로 통지
