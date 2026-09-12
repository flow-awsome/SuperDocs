# 기술 스택 및 컨벤션

> [mastery/00-initial-intake/02-tech-stack-baseline.md](../../../mastery/00-initial-intake/02-tech-stack-baseline.md)의 확정 결과를 반영한다.

## 1. 확정 스택

| 영역 | 기술 | 버전 |
|---|---|---|
| 백엔드 A | TypeScript / NestJS | |
| 백엔드 B | Python / FastAPI | |
| 프론트엔드 | TypeScript / Next.js | |
| DB | PostgreSQL | |
| 캐시/큐 | Redis | |
| 인프라 | AWS | |

## 2. 코딩 컨벤션 — TypeScript / NestJS

- 모듈 구조: `feature` 단위 모듈 (Controller / Service / Repository / DTO 분리)
- 네이밍: 파일 kebab-case, 클래스 PascalCase, 변수/함수 camelCase
- DTO 검증: `class-validator` 필수
- 예외 처리: NestJS 표준 예외 필터 사용, 도메인 예외는 커스텀 Exception 클래스로 분리
- 의존성 주입: 생성자 주입 원칙, 순환 의존 금지

## 3. 코딩 컨벤션 — TypeScript / Next.js

- 라우팅: App Router 기준, `app/` 디렉토리 구조
- 컴포넌트 네이밍: PascalCase, 파일은 kebab-case 또는 컴포넌트명과 동일
- 서버/클라이언트 컴포넌트 경계: 기본 서버 컴포넌트, 상호작용 필요한 leaf만 `"use client"`
- 데이터 페칭: 서버 컴포넌트에서 직접 fetch 우선, 클라이언트 상태는 최소화
- 스타일링: (Tailwind CSS 등 확정 필요)
- API 호출: NestJS/FastAPI 백엔드와의 통신 규약은 [01-architecture/01-system-composition/service-boundary-map.md](../01-system-composition/service-boundary-map.md) 참조

## 4. 코딩 컨벤션 — Python / FastAPI

- 프로젝트 구조: 라우터/서비스/스키마(Pydantic)/리포지토리 계층 분리
- 네이밍: 파일/함수/변수 snake_case, 클래스 PascalCase
- 타입 힌트 필수, `mypy` 또는 `pyright` 통과 기준
- 검증: Pydantic 모델로 입출력 스키마 강제
- 비동기: I/O 바운드 작업은 `async def` 우선

## 5. 공통 컨벤션

- 커밋 메시지: Conventional Commits (`feat:`, `fix:`, `refactor:` 등)
- 브랜치 전략: (확정 필요 — 예: trunk-based / git-flow)
- 린트/포맷: (ESLint+Prettier / Ruff+Black 등 확정)
- 환경변수: `.env`는 커밋 금지, `.env.example`로 키만 관리

## 6. 서비스 간 통신 규칙

권장 기본값(이 하네스의 기본 전제 — 프로젝트 사정에 맞게 확정 후 아래 칸을 채운다):

| 항목 | 권장 기본값 | 이 프로젝트 확정값 |
|---|---|---|
| NestJS ↔ FastAPI 통신 프로토콜 | REST + OpenAPI 스펙 공유 (내부 호출량이 크면 gRPC 검토) | |
| Next.js ↔ 백엔드 통신 방식 | Next.js Route Handler(BFF) 경유 — 클라이언트가 백엔드 URL/토큰을 직접 다루지 않게 함 | |
| 공통 에러 응답 포맷 | RFC 7807 (Problem Details for HTTP APIs) | |
| 인증/인가 전파 방식 | JWT, `Authorization: Bearer` 헤더로 전파. Next.js BFF가 세션 쿠키↔JWT 변환을 맡음 | |

편차나 예외가 필요하면 [07-decisions/01-architecture-decisions](../../07-decisions/01-architecture-decisions/README.md)에 근거를 남긴다.
