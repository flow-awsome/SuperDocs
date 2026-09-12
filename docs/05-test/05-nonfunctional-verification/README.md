# 05-nonfunctional-verification — 비기능 검증

성능, 보안, 가용성, 확장성 등 기능 외적 품질 검증.

## 검증 항목

| 항목 | 기준 | 도구 |
|---|---|---|
| 성능 (응답시간) | [mastery/00-initial-intake/04-success-criteria-and-constraints.md](../../../mastery/00-initial-intake/04-success-criteria-and-constraints.md) 참조 | k6, Locust 등 |
| 부하/스트레스 | 목표 동시 사용자 수 | k6 |
| 가용성 | 목표 SLA | 카오스 테스트 (필요시) |
| DB 쿼리 성능 | 슬로우 쿼리 임계치 | pg_stat_statements |

## 보안 세부 체크리스트 (OWASP Top 10만으로는 부족 — 구체 항목)

각 항목은 [OWASP ASVS](https://owasp.org/www-project-application-security-verification-standard/) 챕터에 매핑한다. AI에 "안전하게 만들어줘" 대신 "ASVS V2 항목 기준으로 인증 구현해줘" 식으로 구체적으로 지시하고, 결과도 해당 챕터 기준으로 검토한다.

| 항목 | 확인 내용 | ASVS 챕터 | 도구/방법 |
|---|---|---|---|
| 인증 | 토큰 만료/재발급, 브루트포스·레이트리밋 | V2 (Authentication) | 수동 점검 + 통합 테스트 |
| 세션 관리 | 세션 고정/탈취 방지 | V3 (Session Management) | 수동 점검 |
| 인가 | 인가 경계(IDOR) — 다른 사용자 리소스 접근 시도 | V4 (Access Control) | 통합 테스트 |
| 입력 검증 | 인젝션(SQL/NoSQL), XSS | V5 (Validation, Sanitization and Encoding) | 정적분석 + 수동 점검 |
| 시크릿 관리 | 키/토큰이 코드·로그·저장소 히스토리에 노출되지 않는가, 로테이션 절차 | V6 (Stored Cryptography) | [05-test/00-static-verification](../00-static-verification/README.md)의 의존성 취약점 스캔과 연동 |
| 로그 마스킹 | 로그에 PII/토큰 등 민감정보가 그대로 찍히지 않는가 | V7 (Error Handling and Logging) | 수동 점검 |
| 의존성 취약점 | 알려진 CVE, 미지원 서드파티 컴포넌트 | V14 (Configuration) | [05-test/00-static-verification](../00-static-verification/README.md) 참조 (여기서 중복 관리하지 않음) |

레벨(L1/L2/L3)은 프로젝트 리스크에 맞게 [mastery/00-initial-intake/04-success-criteria-and-constraints.md](../../../mastery/00-initial-intake/04-success-criteria-and-constraints.md)에서 확정하고 [07-decisions](../../07-decisions/README.md)에 ADR로 남긴다. 위 챕터 번호는 ASVS 버전에 따라 세부 절이 바뀔 수 있으니 적용 시 원문 대조 필수.

## 클라우드 인프라 관점 검증

[01-architecture/00-system-foundation/environment-and-infra-baseline.md](../../01-architecture/00-system-foundation/environment-and-infra-baseline.md)에 정의된 구성이 실제 부하를 견디는지 확인한다. 비용 대비 과설계/과소설계 여부도 함께 판단한다.
