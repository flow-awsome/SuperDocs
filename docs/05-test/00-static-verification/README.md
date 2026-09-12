# 00-static-verification — 정적 검증

코드를 실행하지 않고 잡아내는 문제들: 린트, 타입체크, 정적분석, 의존성 취약점 스캔.

## 도구

| 대상 | 도구 | 통과 기준 |
|---|---|---|
| 백엔드 언어/프레임워크 | (린터, 타입체커 확정) | 에러 0건 |
| 프론트엔드 언어/프레임워크 | (린터, 타입체커 확정) | 에러 0건 |
| 의존성 취약점 | (패키지 매니저별 감사 도구) | High 이상 0건 |

## CI 연동

이 검증은 PR마다 자동 실행되어야 한다 — 파이프라인 구성은 [01-architecture/00-system-foundation/environment-and-infra-baseline.md](../../01-architecture/00-system-foundation/environment-and-infra-baseline.md) 4절 참조.

## 예외 처리

특정 규칙을 예외 처리해야 한다면 인라인 주석 억제만 하지 말고 사유를 여기 기록한다.

| 규칙 | 예외 대상 | 사유 |
|---|---|---|
