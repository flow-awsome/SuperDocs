# 02-system-logic — 시스템 로직

시스템이 "어떻게 동작하는가"의 핵심 도메인 로직과 데이터 흐름을 담는다. 코드 레벨 세부 흐름은 [04-code/01-business-logic](../../04-code/01-business-logic/README.md)에 있고, 이 폴더는 그보다 한 단계 위의 개념적 흐름을 다룬다.

## 파일

- `core-domain-logic.md` — 핵심 도메인 규칙과 불변조건(invariant)
- `data-flow-overview.md` — 요청부터 응답까지, 이벤트 발생부터 처리까지의 전체 흐름

## 작성 원칙

- "이 로직이 왜 이렇게 설계됐는가"는 여기가 아니라 [07-decisions/00-logic-decisions](../../07-decisions/00-logic-decisions/README.md)에 남긴다. 이 폴더는 현재 로직이 **무엇인지**만 담는다.
- Entity의 **이름과 관계 정의**(무엇이 존재하는가)는 [01-architecture/03-system-definition/glossary-and-domain-model.md](../03-system-definition/glossary-and-domain-model.md)가 단일 출처다. 이 폴더의 `core-domain-logic.md`는 그 Entity가 **지켜야 하는 규칙**(불변조건, 상태전이)만 담는다 — 이름을 다시 정의하지 않는다.
