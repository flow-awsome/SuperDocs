# 01-docs-blueprint — 독스 설계도 (인터뷰 → 하네스 설정 변환)

[00-initial-intake](../00-initial-intake/README.md)의 답변은 그 자체로는 아직 `docs/` 구성이 아니다. 이 폴더가 그 답변을 실제 `docs/` 설정값(어떤 모듈을 켤지, 문서 크기 예산을 얼마로 할지, 위험도 임계값을 어디로 잡을지)으로 변환하는 단계다. 이 변환 결과물이 프로젝트의 **"마스터 독스"** — [_template-master-docs-setup-plan.md](_template-master-docs-setup-plan.md)를 채운 최종본 — 다.

## 판단 기준

### 1. 팀/인력 규모 → 감사 렌즈 수

- 1~3인: [docs/11-audit](../../docs/11-audit/README.md)의 10개 렌즈 중 리스크가 큰 3~4개(보안, 비즈니스 로직 전수, 문서-코드 정합성, 아키텍처 정합성)만 선택해 순환 적용.
- 4~10인: 팀별로 렌즈를 1~2개씩 배정, 5~6개 렌즈로 라운드 구성.
- 10인 이상/멀티팀: 10개 렌즈 전체를 팀별로 배정, [docs/AGENTS.md](../../docs/AGENTS.md) 5절의 팀 매핑표와 1:1 대응.

### 2. 위험 허용도 → Lv 임계값

[00-initial-intake/04-success-criteria-and-constraints.md](../00-initial-intake/04-success-criteria-and-constraints.md) 5절의 답변을 [docs/01-architecture/04-system-instructions/agent-operating-rules.md](../../docs/01-architecture/04-system-instructions/agent-operating-rules.md) 7절 표에 그대로 반영한다. 규제 산업/결제/의료 데이터를 다루면 임계값을 낮춘다(더 자주 확인받는다).

### 3. 문서 운영 성숙도 → 거버넌스 엄격도

- 처음 하네스를 도입하는 팀: [docs/00-control-tower/doc-governance-policy.md](../../docs/00-control-tower/doc-governance-policy.md)의 기본 예산값을 그대로 사용.
- 이미 문서가 방대해진 상태에서 마이그레이션하는 팀(예: 기존 프로젝트에 이 하네스를 뒤늦게 도입): 먼저 기존 문서를 폴더별로 분류해 [docs/06-history](../../docs/06-history/README.md)로 옮기고, `archive/YYYY-MM/` 인덱스부터 만든 뒤 새 문서 작성을 시작한다 (한꺼번에 재구성하지 않는다 — 진행 중인 작업을 방해하지 않도록 점진적으로 이관).

### 4. 고객사/멀티테넌트 여부 → 추가 모듈

여러 고객사/파트너별로 별도 요구사항·계약이 존재하면(엔터프라이즈 B2B, 커스텀 컨설팅 계약 등), `docs/`에 `12-customers/{고객코드}/` 모듈을 추가하고 baseline과 충돌하는 지점은 별도 "충돌 로그" 문서로 추적한다. 단일 제품/단일 고객군이면 이 모듈은 생략한다.

### 5. 인프라 규모 → 환경 구성

[00-initial-intake/02-tech-stack-baseline.md](../00-initial-intake/02-tech-stack-baseline.md) 3절의 비용 상한에 따라 [docs/01-architecture/00-system-foundation/environment-and-infra-baseline.md](../../docs/01-architecture/00-system-foundation/environment-and-infra-baseline.md)의 후보 구성 중 하나를 확정한다 — 처음부터 완전한 고가용성 구성을 넣지 않는다 (과설계 방지, [docs/AGENTS.md](../../docs/AGENTS.md) "트레이드오프 저울" 참조).

## 산출물

[_template-master-docs-setup-plan.md](_template-master-docs-setup-plan.md)를 복사해 `master-docs-setup-plan.md`로 완성한다. 이 문서가 mastery 인터뷰의 최종 결과물이며, 이후 `docs/`를 실제로 채우는 작업 지시서 역할을 한다.
