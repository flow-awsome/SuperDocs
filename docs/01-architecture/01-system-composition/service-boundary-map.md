# 서비스 경계 지도

## 외부 경계 (Context 레벨)

이 시스템 바깥에서 상호작용하는 행위자/외부 시스템. C4 모델의 Context 레벨에 대응 — 아래 "서비스 목록"이 내부 Container/Component를 다룬다면, 이 절은 "이 시스템이 무엇과 마주하고 있는가"를 먼저 고정한다.

| 외부 행위자/시스템 | 관계 | 데이터 방향 |
|---|---|---|
| (예: 최종 사용자) | | |
| (예: 결제 PG사) | | |
| (예: 외부 API/SaaS) | | |

> **다른 Git 저장소로 나뉜 형제 프로젝트**(예: 이 저장소가 백엔드 A이고, 프론트엔드·백엔드 B가 별도 저장소인 경우)는 이 표가 아니라 [related-repositories.md](related-repositories.md)에 등록한다 — 이 표는 "이 저장소 하나가 마주하는 제3자"를, `related-repositories.md`는 "같은 시스템을 이루는 다른 저장소"를 다룬다.

## 서비스 목록 (이 저장소 내부)

| 서비스명 | 언어/프레임워크 | 책임 범위 | 소유 DB/스키마 |
|---|---|---|---|
| | (백엔드 도메인 A) | | |
| | (백엔드 도메인 B, 있는 경우) | | |

## 서비스 간 통신 (이 저장소 내부)

다른 저장소의 서비스를 호출/피호출하는 경우는 여기가 아니라 [related-repositories.md](related-repositories.md)와 [04-code/02-api-contracts](../../04-code/02-api-contracts/README.md)에서 다룬다. 프로토콜/에러포맷/인증전파의 **기본값**은 [00-system-foundation/tech-stack-and-conventions.md](../00-system-foundation/tech-stack-and-conventions.md) 6절 참조. 아래 표는 그 기본값을 따라 실제로 어느 서비스가 어느 서비스를 부르는지만 매핑한다 (기본값에서 벗어나는 예외만 "프로토콜" 칸에 별도로 적는다).

| 호출자 | 대상 | 프로토콜(기본값과 다르면만 기재) | 동기/비동기 |
|---|---|---|---|
| 프론트엔드 (BFF) | 백엔드 도메인 A | (기본값) | 동기 |
| 백엔드 도메인 A | 백엔드 도메인 B (있는 경우) | (기본값) | 동기 |

## 데이터 소유권 원칙

- 한 테이블/스키마는 원칙적으로 한 서비스가 소유한다 (직접 조인 금지, API 경유).
- 예외가 필요하면 [07-decisions/01-architecture-decisions](../../07-decisions/01-architecture-decisions/README.md)에 근거를 남긴다.

## 장애 격리 경계

- 한 서비스 장애가 다른 서비스에 전파되지 않도록 하는 지점 (서킷 브레이커, 큐 버퍼링 등)
