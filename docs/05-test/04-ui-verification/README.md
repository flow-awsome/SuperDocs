# 04-ui-verification — UI 검증

Next.js 화면의 시각적/기능적/접근성 검증.

## 검증 항목

| 항목 | 방법 |
|---|---|
| 컴포넌트 단위 렌더링 | React Testing Library |
| 시각적 회귀 | 스크린샷 비교 (Chromatic 등, 도입 여부 확정) |
| 반응형 | 주요 breakpoint 수동/자동 검증 |
| 접근성 | axe 등 자동 스캔 + 수동 키보드 내비게이션 |
| 크로스 브라우저 | 대상 브라우저 목록 확정 |

## 관련 사용자 흐름

[02-scenario/02-user-flows](../../02-scenario/02-user-flows/README.md) 기준으로 화면별 검증 체크리스트를 구성한다.
