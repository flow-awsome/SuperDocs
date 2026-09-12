# 재검수 체크리스트 (누적, append-only)

일반적인 통합 테스트는 "새 기능이 동작하는가"를 확인한다. 이 문서는 그것과 별개로 **"이전에 위험했던 지점이 이번 변경으로 다시 깨지지 않았는가"**를 확인하는 짧고 구체적인 체크 목록이다. 테넌트 격리, 권한 경계, 인증 우회처럼 한 번이라도 실제 취약점/버그가 났던 영역은 새 기능을 추가할 때마다 재확인 없이 넘어가면 조용히 재발한다.

## 사용 원칙

- 이 목록은 **줄지 않는다.** 항목을 지우지 않고, 더 이상 관련 없어지면 "폐기됨(사유)"로 표시만 한다.
- 새 항목은 실제로 문제가 발견됐거나(트러블슈팅에서 승격) [11-audit](../../11-audit/README.md) 감사에서 지적됐을 때만 추가한다 — 예방 차원의 막연한 체크리스트가 아니라 **실제로 한 번 뚫렸거나 뚫릴 뻔했던 지점**만 남긴다.
- [01-architecture/04-system-instructions/agent-operating-rules.md](../../01-architecture/04-system-instructions/agent-operating-rules.md) 7절의 **Lv8-9 등급 작업은 완료 전 이 목록 전체를 재실행**한다 (해당 항목이 있다면).

## 항목 형식

```
### (알파벳 또는 번호) — (한 줄 제목)
- 추가일:
- 계기: (어떤 트러블/감사에서 파생됐는지 링크)
- 확인 대상: (구체적으로 무엇이 다시 깨지면 안 되는가)
- 확인 방법: (실제 커맨드 또는 grep 패턴 — 실행 가능한 수준으로)
- 최근 재확인일:
```

## 목록

### (a) — 예시: 테넌트 간 데이터 격리

- 추가일: (예시 항목 — 실제 프로젝트에서 첫 항목이 생기면 이 예시는 지운다)
- 계기: (예: RLS 정책 우회 버그를 겪은 트러블슈팅 문서 링크)
- 확인 대상: 한 테넌트의 요청이 다른 테넌트의 데이터에 접근 가능한지
- 확인 방법: `pnpm test:integration -- tenant-isolation` (프로젝트에 맞게 실제 커맨드로 교체)
- 최근 재확인일:

## 관련 문서

- 발견 계기: [08-troubleshooting](../../08-troubleshooting/README.md)
- 감사에서 파생된 경우: [11-audit/01-audit-reports](../../11-audit/01-audit-reports/README.md)
- 이 체크리스트 자체의 존재 이유(위험도별 재검증 의무): [01-architecture/04-system-instructions/agent-operating-rules.md](../../01-architecture/04-system-instructions/agent-operating-rules.md) 7절
