# 환경 및 인프라 베이스라인

## 1. 환경 구성

| 환경 | 목적 | 인프라 규모 | 접근 권한 |
|---|---|---|---|
| local | 개발자 로컬 | Docker Compose (Postgres, Redis) | 개발자 전원 |
| staging | 통합 검증 | 프로덕션 축소판 | 개발팀 + QA |
| production | 실서비스 | [mastery/00-initial-intake/02-tech-stack-baseline.md](../../../mastery/00-initial-intake/02-tech-stack-baseline.md) 확정 규모 | 최소 권한 원칙 |

## 2. AWS 인프라 베이스라인

> 완결성과 비용 산정을 함께 고려한 최종 구성. 초기 산정 근거는 [mastery/00-initial-intake/02-tech-stack-baseline.md](../../../mastery/00-initial-intake/02-tech-stack-baseline.md) 3절 참조.

- 리전:
- VPC/서브넷 구조:
- 컴퓨트: (ECS Fargate / EKS / Lambda 중 확정)
- DB: RDS PostgreSQL — 인스턴스 클래스, Multi-AZ 여부
- 캐시: ElastiCache Redis — 노드 타입/개수
- 로드밸런싱/CDN: ALB, CloudFront
- 시크릿 관리: AWS Secrets Manager / Parameter Store
- 관측성: CloudWatch 대시보드, 알람 임계치 → [05-test/06-environment-verification](../../05-test/06-environment-verification/README.md)와 연동

## 3. 월간 예상 비용 추정

| 구성요소 | 예상 월 비용 | 산정 근거 |
|---|---|---|
| | | |

비용 재산정 이력은 [06-history](../../06-history/README.md)에 기록한다.

## 3.5 비용 재검토 정책

- **기본 트리거**: 페이즈 종료마다 + 실제 지출이 예산의 20%를 초과하는 순간 즉시.
- 재검토 결과는 [00-control-tower/project-dashboard.md](../../00-control-tower/project-dashboard.md)의 "인프라/비용 상태" 표에 반영한다.
- 구성 변경(예: 저비용 티어 → 엔터프라이즈 티어 승격)은 [07-decisions/01-architecture-decisions](../../07-decisions/01-architecture-decisions/README.md)에 ADR로 남긴다.

## 4. CI/CD 파이프라인 개요

- 빌드/테스트/배포 단계 구성
- 배포 전략: (블루-그린 / 롤링 / 카나리)
- 롤백 절차 → [08-troubleshooting](../../08-troubleshooting/README.md)와 연동
