# 00-initial-intake — 최초 프로젝트 인테이크

프로젝트 착수 시점에 **한 번** 깊이 있게 진행하는 설문/인터뷰 묶음이다. 여기서 얻은 답변이 [docs/AGENTS.md](../../docs/AGENTS.md), [docs/01-architecture](../../docs/01-architecture/README.md), [docs/02-scenario](../../docs/02-scenario/README.md)의 초기 뼈대가 된다. 이 인터뷰가 끝난 뒤 실제로 어떤 `docs/` 구성을 켤지는 [01-docs-blueprint](../01-docs-blueprint/README.md)에서 정한다.

## 진행 순서

1. [01-project-questionnaire.md](01-project-questionnaire.md) — 서비스 정체성, 목표, 범위
2. [02-tech-stack-baseline.md](02-tech-stack-baseline.md) — 기술 스택 확정 및 편차 기록
3. [03-stakeholder-and-scope.md](03-stakeholder-and-scope.md) — 이해관계자, 의사결정 권한, 범위 경계
4. [04-success-criteria-and-constraints.md](04-success-criteria-and-constraints.md) — 성공 기준, 제약조건(예산/기한/컴플라이언스)

## 사용 방법

- 각 파일은 질문지 + 답변을 함께 담는다. AI는 질문을 던지고, 사용자 답변을 그대로/요약해서 채워 넣는다.
- 인테이크가 끝나면 [docs/AGENTS.md](../../docs/AGENTS.md)의 "프로젝트 정체성" 섹션과 "기술 스택 기본값" 섹션을 이 폴더 내용을 근거로 갱신한다.
- 인테이크 이후 스택이나 범위가 바뀌면, 이 폴더의 원본을 고치지 말고 [docs/06-history](../../docs/06-history/README.md)에 변경 이력을 남긴 뒤 여기 문서를 갱신한다 (원본을 덮어쓰기만 하면 "왜 바뀌었는지"가 사라진다).
