# 서비스 경계 지도

## 서비스 목록

| 서비스명 | 언어/프레임워크 | 책임 범위 | 소유 DB/스키마 |
|---|---|---|---|
| | NestJS | | |
| | FastAPI | | |

## 서비스 간 통신

프로토콜/에러포맷/인증전파의 **기본값**은 [00-system-foundation/tech-stack-and-conventions.md](../00-system-foundation/tech-stack-and-conventions.md) 6절 참조. 아래 표는 그 기본값을 따라 실제로 어느 서비스가 어느 서비스를 부르는지만 매핑한다 (기본값에서 벗어나는 예외만 "프로토콜" 칸에 별도로 적는다).

| 호출자 | 대상 | 프로토콜(기본값과 다르면만 기재) | 동기/비동기 |
|---|---|---|---|
| Next.js (BFF) | NestJS | (기본값) | 동기 |
| NestJS | FastAPI | (기본값) | 동기 |

## 데이터 소유권 원칙

- 한 테이블/스키마는 원칙적으로 한 서비스가 소유한다 (직접 조인 금지, API 경유).
- 예외가 필요하면 [07-decisions/01-architecture-decisions](../../07-decisions/01-architecture-decisions/README.md)에 근거를 남긴다.

## 장애 격리 경계

- 한 서비스 장애가 다른 서비스에 전파되지 않도록 하는 지점 (서킷 브레이커, 큐 버퍼링 등)
