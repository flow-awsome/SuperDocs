# 모듈 구성 지도

## NestJS 서비스: (서비스명)

```mermaid
graph TD
  AppModule --> AuthModule
  AppModule --> UserModule
  AppModule --> "..."
```

| 모듈 | 책임 | 의존 모듈 |
|---|---|---|
| AuthModule | 인증/토큰 발급 (예시 행 — 실제 모듈로 교체) | UserModule |

데이터 소유권은 여기 적지 않는다 — [service-boundary-map.md](service-boundary-map.md)가 단일 출처다.

## FastAPI 서비스: (서비스명)

| 라우터/모듈 | 책임 | 의존 모듈 |
|---|---|---|
| | | |

## Next.js 앱: (앱명)

| 라우트 세그먼트 | 책임 | 호출 백엔드 API | 렌더링 전략 |
|---|---|---|---|
| | | | |

## 신규 모듈 추가 규칙

- 새 모듈이 기존 모듈과 책임이 겹치는지 먼저 이 표에서 확인
- 추가 후 이 문서와 [04-code/00-module-map](../../04-code/00-module-map/README.md) 동시 갱신
