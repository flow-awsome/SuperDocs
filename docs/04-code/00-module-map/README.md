# 00-module-map — 모듈 지도

실제 저장소의 디렉토리 구조와 [01-architecture/01-system-composition](../../01-architecture/01-system-composition/README.md)의 설계상 모듈 구성이 어떻게 매핑되는지 기록한다.

## 템플릿

[_template-module-map.md](_template-module-map.md) — 서비스(리포지토리)별로 하나씩 생성한다.

## 작성 원칙

- 실제 디렉토리 트리 전체를 복사하지 않는다 (금방 낡는다). 대신 "이 종류의 로직은 이 디렉토리에 있다"는 규칙과 대표 경로만 남긴다.
- 모노레포인 경우 서비스별 최상위 경로도 명시한다.
