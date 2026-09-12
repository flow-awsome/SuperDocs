# 기술 스택 및 컨벤션

> [mastery/00-initial-intake/02-tech-stack-baseline.md](../../../mastery/00-initial-intake/02-tech-stack-baseline.md)의 확정 결과를 반영한다. 이 하네스는 특정 언어·프레임워크를 전제하지 않으므로 아래는 채워 넣는 골격이다.

## 1. 확정 스택

| 영역 | 기술 | 버전 |
|---|---|---|
| 백엔드 (도메인 A) | | |
| 백엔드 (도메인 B, 있는 경우) | | |
| 프론트엔드 | | |
| DB | | |
| 캐시/큐 | | |
| 인프라 | | |

## 2. 코딩 컨벤션 — 백엔드 (도메인 A)

- 모듈 구조 원칙: (feature 단위 / 계층형 등)
- 네이밍 규칙: 파일 / 클래스 / 변수·함수
- 입력 검증 방식
- 예외 처리 원칙: 표준 예외 vs 도메인 커스텀 예외 분리
- 의존성 주입/구성 원칙

## 3. 코딩 컨벤션 — 프론트엔드

- 라우팅/디렉토리 구조
- 컴포넌트 네이밍 규칙
- 서버/클라이언트 렌더링 경계 (해당하는 경우)
- 데이터 페칭 전략
- 스타일링 방식
- 백엔드 API 호출 규약: [01-architecture/01-system-composition/service-boundary-map.md](../01-system-composition/service-boundary-map.md) 참조

## 4. 코딩 컨벤션 — 백엔드 (도메인 B, 있는 경우)

- 프로젝트 구조 (계층 분리)
- 네이밍 규칙
- 타입/스키마 검증 방식
- 비동기 처리 원칙

## 5. 공통 컨벤션

- 커밋 메시지: Conventional Commits (`feat:`, `fix:`, `refactor:` 등)
- 브랜치 전략: (확정 필요 — 예: trunk-based / git-flow)
- 린트/포맷 도구: (확정 필요)
- 환경변수: `.env`는 커밋 금지, `.env.example`로 키만 관리

## 6. 서비스 간 통신 규칙

| 항목 | 권장 기본값 | 이 프로젝트 확정값 |
|---|---|---|
| 서비스 간 통신 프로토콜 | REST + OpenAPI 스펙 공유 (내부 호출량이 크면 gRPC 검토) | |
| 프론트엔드 ↔ 백엔드 통신 방식 | BFF 경유 — 클라이언트가 백엔드 URL/토큰을 직접 다루지 않게 함 | |
| 공통 에러 응답 포맷 | RFC 7807 (Problem Details for HTTP APIs) | |
| 인증/인가 전파 방식 | 토큰 기반, `Authorization: Bearer` 헤더로 전파 | |

편차나 예외가 필요하면 [07-decisions/01-architecture-decisions](../../07-decisions/01-architecture-decisions/README.md)에 근거를 남긴다.
