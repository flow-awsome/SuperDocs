# 08-verification-setup — 검증 세팅 방법

위 검증 폴더들을 실행하기 위한 환경 구축 가이드. "어떻게 실행하는가"에 집중한다 (무엇을 검증하는가는 각 폴더 참조).

## 1. 로컬 인프라 (Docker Compose 예시)

```yaml
# docker-compose.yml (프로젝트 루트, 골격 — 실제 이미지/버전/포트는 확정한 스택에 맞게 채운다)
services:
  db:
    image: (확정 필요)
    ports: ["(포트)"]
  cache:
    image: (확정 필요)
    ports: ["(포트)"]
```

실행: `docker compose up -d`

## 2. 검증 유형별 실행 커맨드 (확정한 스택의 실제 커맨드로 채운다)

| 검증 유형 | 커맨드 |
|---|---|
| [00-static-verification](../00-static-verification/README.md) | (확정 필요) |
| [01-unit-verification](../01-unit-verification/README.md) | (확정 필요) |
| [02-integration-verification](../02-integration-verification/README.md) | (확정 필요, DB/캐시 기동 필요) |
| [03-scenario-verification](../03-scenario-verification/README.md) | (확정 필요) |

이 표는 채워 넣는 즉시 실제 프로젝트의 정확한 커맨드로 교체한다 — 빈칸 그대로 방치하지 않는다.

## 3. 로컬 `.env` 최소 구성

- `DATABASE_URL=(확정한 DB 접속 문자열 형식)`
- 캐시 접속 URL (확정한 캐시 종류에 맞게)
- 그 외 시크릿은 `.env.example`에 키 이름만 커밋하고, 실제 값은 로컬에서 채운다.

## 4. 테스트 데이터 시딩

(프로젝트별 시딩 스크립트 경로와 실행 커맨드를 여기에 채운다.)

## 새 팀원/새 AI 세션 온보딩

이 문서 하나만 보고 모든 검증을 로컬에서 재현할 수 있어야 한다. **위 1~4절이 예시 상태로 비어있는 동안은 이 목표가 아직 달성되지 않은 것으로 간주한다** — 실제로 한 번 실행해 검증한 내용으로 채워야 "완료"다. 재현이 안 되는 사례가 생기면 [08-troubleshooting](../../08-troubleshooting/README.md)에 기록하고 이 문서를 보강한다.
