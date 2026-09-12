# 모듈 지도: (서비스/리포지토리명)

- 프레임워크: NestJS / FastAPI / Next.js
- 리포지토리 경로: (모노레포 내 경로 또는 저장소 URL)

## 디렉토리 규칙

| 디렉토리 | 이 종류의 코드가 위치함 | 대표 예시 경로 |
|---|---|---|
| `src/modules/*` | 기능 모듈 (Controller/Service/DTO) | |
| `src/common/guards/*` | 인증/인가 가드 | |
| `src/common/interceptors/*` | 로깅/응답 변환 등 인터셉터 | |
| `src/common/pipes/*` | 검증/변환 파이프 | |
| `src/common/*` (그 외) | 공통 유틸/미들웨어 | |
| `src/config/*` | 환경설정 | |
| `packages/shared-types/*` (모노레포인 경우) | 서비스 간 공유 타입 | |

## [01-architecture/01-system-composition](../../01-architecture/01-system-composition/README.md)와의 매핑

| 설계상 모듈 | 실제 디렉토리 |
|---|---|
| | |

어긋남이 발견되면 설계 문서를 갱신하거나, 코드 리팩터링이 필요하면 [03-plan](../../03-plan/README.md)에 작업으로 등록한다.
