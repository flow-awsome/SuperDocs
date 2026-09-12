# 관련 프로젝트/저장소 확인

이 프로젝트가 다른 Git 저장소와 동시에 개발되는 다각적 구성(멀티레포)의 일부인지 확인한다. 예: 통합 프론트엔드 1개 + 이를 지원하는 서로 다른 백엔드 3개가 각자 별도 저장소에서 이 하네스를 쓰는 경우. **해당 없으면 1절에 "해당 없음"만 남기고 다음 문서로 넘어간다.**

## 1. 이 구성의 형태

- 이 프로젝트는 몇 개의 저장소로 구성된 시스템의 일부인가?
- 그중 이 저장소가 맡는 역할은? (예: 통합 프론트엔드 / 백엔드 도메인 A / 백엔드 도메인 B)
- 각 저장소도 이 하네스(SuperDocs)를 쓰고 있는가, 아니면 이 저장소만 쓰는가? (상대가 이 하네스를 안 써도 아래 레지스트리는 동일하게 작동한다 — 링크가 가리키는 대상이 이 하네스 형식이 아닐 뿐)

## 2. 관련 저장소 레지스트리

| 저장소명 | 역할 | Git URL | 이 저장소와의 관계 | 접근 가능 여부 |
|---|---|---|---|---|
| | | | 소비 / 제공 / 양방향 | public(WebFetch 가능) / private(같은 조직, `gh` 접근 가능) / private(접근 불가 — 사용자에게 물어야 함) |

## 3. 다음 단계

- 이 표는 [docs/01-architecture/01-system-composition/related-repositories.md](../../docs/01-architecture/01-system-composition/related-repositories.md)로 승격하면서, 각 저장소별로 "조사 시 우선 참조할 문서"(구체적 파일 링크)를 채운다.
- 이후 착수/조사 방식은 [01-architecture/04-system-instructions/agent-operating-rules.md](../../docs/01-architecture/04-system-instructions/agent-operating-rules.md)의 관련 저장소 조사 원칙을 따른다 — 매 세션 전체를 읽지 않고, 경계에 걸친 작업이 생길 때만 필요한 문서만 그때그때 조사한다(JIT).
