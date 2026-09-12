# 12-customers — 고객사별 트랙 (선택 모듈)

**이 폴더는 기본적으로 비어있어도 된다.** 단일 제품/단일 사용자군 서비스라면 사용하지 않는다. 여러 고객사(B2B 엔터프라이즈, 파트너별 커스텀 계약 등)를 대상으로 서비스하며, 고객사마다 별도 요구사항·컨설팅·검증이 필요하다면 이 폴더를 사용한다. 사용 여부는 [mastery/01-docs-blueprint](../../mastery/01-docs-blueprint/README.md)의 3절에서 결정한다.

## 왜 baseline과 분리하는가

고객사 한 곳만의 요구사항이 [01-architecture](../01-architecture/README.md)나 [02-scenario](../02-scenario/README.md) 같은 공통 baseline 문서에 섞이면, "이게 모든 고객에게 적용되는 표준인지 이 고객만의 예외인지" 구분이 안 된다. 이 폴더는 고객사별로 완전히 분리해, baseline은 항상 "모든 고객 공통"만 담게 한다.

## 구조

```
12-customers/
└── {고객코드}/
    ├── README.md            -- 이 고객사 개요, baseline과의 관계
    ├── survey/              -- 이 고객사 전용 요구사항 설문/인터뷰
    ├── consulting/          -- 이 고객사와의 컨설팅 세션 기록
    ├── history/             -- 이 고객사 관련 변경 이력
    └── conflict-and-improvement-log.md  -- baseline과 충돌하는 지점, 그 처리 결과
```

## 템플릿

[_template-client](_template-client/README.md) 폴더를 복사해 `{고객코드}/`로 이름을 바꿔 사용한다.

## 작성 원칙

- baseline과 충돌하는 요구사항은 반드시 `conflict-and-improvement-log.md`에 기록하고, baseline을 바꾸기로 했다면 [07-decisions](../07-decisions/README.md)에도 ADR을 남긴다 (이 고객사만의 예외인지, 모든 고객에게 적용할 개선인지 명확히 구분).
- 특정 고객사만 아는 민감한 계약 정보(가격, SLA 등)는 접근 권한을 별도로 관리한다 — 이 폴더 구조 자체는 접근 통제를 대신하지 않는다.
