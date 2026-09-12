# 기술 스택 베이스라인 확정

이 하네스의 기본값(TypeScript/Python, NestJS/FastAPI, PostgreSQL, Redis, AWS)을 이 프로젝트에 그대로 적용할지, 편차를 둘지 확정한다. 확정된 내용은 [docs/AGENTS.md](../../docs/AGENTS.md) 2절과 [docs/01-architecture/00-system-foundation/tech-stack-and-conventions.md](../../docs/01-architecture/00-system-foundation/tech-stack-and-conventions.md)에 반영한다.

## 1. 언어/프레임워크

| 영역 | 하네스 기본값 | 이 프로젝트 확정값 | 편차 사유 |
|---|---|---|---|
| 백엔드 (도메인 A) | TypeScript / NestJS | | |
| 백엔드 (도메인 B, 데이터/ML 등) | Python / FastAPI | | |
| 프론트엔드 | TypeScript / Next.js | | |
| 모바일 | (미정) | | |

- NestJS와 FastAPI를 어떤 기준으로 도메인 분리할 것인가? (예: 일반 CRUD/트랜잭션 서비스는 NestJS, 데이터 처리/ML/비동기 워커는 FastAPI)
- 두 서비스 간 통신 방식은? (REST / gRPC / 메시지 큐)
- Next.js 렌더링 전략: SSR / SSG / ISR / CSR 중 화면별 기준
- Next.js에서 NestJS/FastAPI API 호출 방식: Route Handler 경유 vs 클라이언트 직접 호출, 인증 토큰 전파 방식

## 2. 데이터 계층

- PostgreSQL 버전 및 확장(extension) 사용 여부 (예: pgvector, PostGIS)
- 스키마 관리 도구 (Prisma / TypeORM / Alembic 등)
- Redis 용도 분리: 캐시 / 세션 / 큐(BullMQ, Celery) / 분산 락 — 각각 명시
- 데이터 백업/복구 정책 초안

## 3. 인프라 (AWS) — 완결성과 비용의 균형

이 하네스는 AWS를 기본 전제로 하되, **완결성만 좇지 않고 비용 산정 기준을 항상 함께 명시**한다.

| 구성 요소 | 최저비용 시작 티어 (1인/저예산) | 표준 엔터프라이즈 티어 | 비용 관점 | 이 프로젝트 결정 |
|---|---|---|---|---|
| 컴퓨트 | Lightsail 단일 인스턴스 (~$10-40/월) 또는 EC2 t3.micro(프리티어) | ECS Fargate / EKS / Lambda | Fargate가 EKS보다 관리비용↓, Lambda는 트래픽 낮을 때 최저비용 | |
| DB | RDS db.t4g.micro Single-AZ (~$15-25/월) | RDS Multi-AZ / Aurora | Aurora가 RDS 대비 비용↑, 초기엔 RDS 단일 AZ로 시작 검토 | |
| 캐시 | 컴퓨트 인스턴스에 Redis 동거(별도 서비스 없이) | ElastiCache Redis (관리형, 장애복구) | 노드 크기/개수에 비례 | |
| 스토리지 | S3 (표준 티어 그대로, 처음부터 저비용) | S3 + 스토리지 클래스 정책 | 사실상 무제한, 저비용 | |
| 네트워크 | 공인 IP 인스턴스 직접 서비스 (ALB/NAT 없음) | VPC, ALB, CloudFront | 보안 격리, NAT Gateway 비용 주의 | |
| 관측성 | 인스턴스 로그 파일 + 기본 CloudWatch 무료 티어 | CloudWatch, X-Ray | 장애 대응 속도↑, 로그 보존 기간에 비례해 비용 증가 | |
| CI/CD | GitHub Actions (무료 티어) | GitHub Actions / CodePipeline | | |

- 이번 페이즈에서 **과설계를 피해야 할 영역**은 어디인가? (예: 초기에는 Aurora 대신 RDS 단일 인스턴스로 시작, ALB/NAT 없이 공인 IP로 직접 서비스)
- 예상 월 인프라 예산 상한선은?
- 비용 재검토 주기는? 기본값: **페이즈 종료마다 + 예상 예산 20% 초과 시 즉시** — [docs/01-architecture/00-system-foundation/environment-and-infra-baseline.md](../../docs/01-architecture/00-system-foundation/environment-and-infra-baseline.md) "비용 재검토 정책" 절과 [docs/06-history](../../docs/06-history/README.md)에 비용 변화 기록

## 4. 편차 승인

편차가 있다면 사유와 함께 [docs/07-decisions/01-architecture-decisions](../../docs/07-decisions/01-architecture-decisions/README.md)에 ADR로 기록한다.
