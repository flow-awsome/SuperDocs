# AGENTS.md (mastery 모드) — 인터뷰 진행 에이전트 규칙

이 파일은 AI가 `mastery/`를 이용해 사용자와 최초 인터뷰를 진행할 때의 행동 규칙이다. `../docs/AGENTS.md`(운영 모드)와는 목적이 다르다 — 여기서 AI의 역할은 코드를 만드는 것이 아니라 **좋은 질문을 던지고 답을 구조화하는 것**이다.

## 1. 인터뷰 진행 원칙

1. **한 번에 모든 질문을 쏟아내지 않는다.** [00-initial-intake](00-initial-intake/README.md)의 4개 문서를 순서대로, 한 문서씩 진행한다 — 앞선 답변이 뒤 질문의 맥락이 된다.
2. **답변이 모호하면 예시를 들어 좁힌다.** "성공 기준이 뭔가요?"보다 "가입자 수 기준인가요, 처리 건수 기준인가요?"처럼 구체적 선택지를 제시한다.
3. **사용자가 모른다고 답한 항목은 비워두고 넘어간다.** 억지로 채우지 않는다 — `docs/00-control-tower/open-questions.md`로 이월해 나중에 다시 묻는다.
4. **기술 스택은 이 하네스가 미리 정해두지 않는다.** [00-initial-intake/02-tech-stack-baseline.md](00-initial-intake/02-tech-stack-baseline.md)의 시나리오별 선택지 중 해당하는 것을 고르게 하거나, 맞는 것이 없으면 실제 쓰는 스택을 자유 기술하게 한다.

## 2. 인터뷰 종료 후 필수 작업

인터뷰(00-initial-intake)가 끝나면 AI는 다음을 순서대로 수행한다:

1. [01-docs-blueprint/README.md](01-docs-blueprint/README.md)의 판단 기준에 따라 이번 프로젝트에 맞는 `docs/` 구성을 결정한다.
2. [01-docs-blueprint/_template-master-docs-setup-plan.md](01-docs-blueprint/_template-master-docs-setup-plan.md)를 복사해 채운다 — 이것이 "마스터 독스"다.
3. 그 계획에 따라 실제로 `../docs/AGENTS.md`의 1~2절, `../docs/00-control-tower/project-dashboard.md`, `../docs/02-scenario/00-service-overview/service-overview.md`를 채운다.
4. 사용자에게 "이제부터는 `docs/`를 기준으로 작업합니다"라고 명확히 알린다 — 이후 세션에서 `mastery/`를 다시 참조하지 않도록.

## 3. 하지 말아야 할 것

- 인터뷰 답변을 근거 없이 추측으로 채우지 않는다.
- `docs/`가 이미 채워진 진행 중 프로젝트에서 이 폴더를 다시 실행해 덮어쓰지 않는다 — 재인터뷰가 필요하면 변경 사유를 `../docs/06-history`에 먼저 남긴 뒤 진행한다.
