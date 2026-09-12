# 01-system-composition — 시스템 구성

시스템이 어떤 모듈/서비스로 나뉘고 어떻게 경계를 이루는지를 담는다. "왜 이렇게 나눴는지"의 판단 근거는 [07-decisions/01-architecture-decisions](../../07-decisions/01-architecture-decisions/README.md)에 있다.

## 파일

- `module-composition-map.md` — NestJS/FastAPI/Next.js 각 서비스 **내부** 모듈 지도 (어떤 모듈이 있는가)
- `service-boundary-map.md` — 서비스 **간** 경계, 통신 방식, 데이터 소유권 (누가 무엇을 부르고 소유하는가)

두 문서 다 "통신"을 다루지만 층위가 다르다: **통신 프로토콜의 정책/컨벤션**(무엇을 기본값으로 쓸지)은 [00-system-foundation/tech-stack-and-conventions.md](../00-system-foundation/tech-stack-and-conventions.md) 6절이 단일 출처이고, 이 폴더의 `service-boundary-map.md`는 그 정책에 따라 **실제 어떤 서비스가 어떤 서비스를 부르는지의 매핑**만 담는다. 데이터 소유권도 `service-boundary-map.md`가 단일 출처다 — `module-composition-map.md`에는 소유권을 중복 기재하지 않는다.

## 작성 원칙

- 다이어그램은 텍스트 기반(mermaid 등)으로 작성해 diff 추적이 가능하게 한다.
- 모듈 경계 변경 시 [04-code/00-module-map](../../04-code/00-module-map/README.md)와 반드시 동기화한다 (설계와 실제 코드 구조가 어긋나지 않게).
