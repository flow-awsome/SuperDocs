# 성공 기준 및 제약조건

## 1. 성공 기준 (Definition of Success)

- 이 프로젝트/페이즈가 "성공"이라고 말할 수 있는 정량적 기준은?
  - 비즈니스 지표 (예: 전환율, 가입자 수, 처리 건수)
  - 기술 지표 (예: 응답시간 p95, 에러율, 가용성)
- 각 지표는 [docs/05-test/05-nonfunctional-verification](../../docs/05-test/05-nonfunctional-verification/README.md)의 비기능 검증 기준으로 연결한다.

### 기술 지표 누락 방지 — ISO/IEC 25010 품질특성 체크

자유 서술만으로는 매번 같은 특성만 챙기고 다른 특성은 잊기 쉽다. 아래 8특성 각각에 대해 "이번 프로젝트에서 다룬다 / 의도적으로 스코프 밖" 중 하나를 명시한다. 다루는 항목만 위 기술 지표와 [05-nonfunctional-verification](../../docs/05-test/05-nonfunctional-verification/README.md)에 연결한다.

| 품질특성 | 다룸/스코프 밖 | 비고 |
|---|---|---|
| 기능적합성 (Functional Suitability) | | |
| 성능효율성 (Performance Efficiency) | | |
| 호환성 (Compatibility) | | |
| 사용성 (Usability) | | |
| 신뢰성 (Reliability) | | |
| 보안성 (Security) | | |
| 유지보수성 (Maintainability) | | |
| 이식성 (Portability) | | |

## 2. 제약조건

| 종류 | 내용 | 영향 범위 |
|---|---|---|
| 예산 | 월 인프라 상한 | [02-tech-stack-baseline.md](02-tech-stack-baseline.md) |
| 기한 | 페이즈별 마일스톤 | [docs/03-plan/00-phases](../../docs/03-plan/00-phases/README.md) |
| 컴플라이언스/보안 | 개인정보, 결제 규제 등 | [docs/01-architecture](../../docs/01-architecture/README.md), [docs/05-test/05-nonfunctional-verification](../../docs/05-test/05-nonfunctional-verification/README.md) |
| 팀 규모/스킬셋 | 가용 인력, 숙련도 | [docs/03-plan](../../docs/03-plan/README.md) 일정 산정 |

## 3. 완료 시 하지 않을 일 (Non-goals)

- 이번 페이즈에서 의도적으로 유예하는 항목과 그 이유

## 4. 리스크 사전 식별

| 리스크 | 발생 시 영향 | 완화 전략 | 관련 문서 |
|---|---|---|---|
| | | | |

## 5. 위험도 등급별 개입 기준 (Lv 임계값)

[docs/01-architecture/04-system-instructions/agent-operating-rules.md](../../docs/01-architecture/04-system-instructions/agent-operating-rules.md) 7절의 위험도(Lv 1-9) 등급표를 이 프로젝트에 맞게 조정한다.

- 착수 전 사용자 확인이 필수가 되는 최소 등급은? (기본값 Lv6 — 위험 회피 성향이 강하면 낮추고, 속도가 우선이면 높인다)
- 완료 후 다음 [docs/11-audit](../../docs/11-audit/README.md) 라운드 재검증이 필수가 되는 최소 등급은? (기본값 Lv8)
- 이 프로젝트에서 "되돌리기 어려움"의 기준은 무엇인가? (예: 프로덕션 데이터 변경, 과금에 영향, 외부에 공개된 API 계약 변경)

확정되면 [docs/07-decisions](../../docs/07-decisions/README.md)에 ADR로 남긴다.

이 문서 갱신 시 [docs/AGENTS.md](../../docs/AGENTS.md)의 "핵심 성공 기준" 섹션도 함께 갱신한다.
