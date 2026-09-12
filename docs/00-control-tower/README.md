# 00-control-tower — 관제탑

프로젝트가 길어지면 문서는 반드시 쌓인다. 이 폴더의 존재 이유는 단 하나 — **사람이 5분 안에 "지금 이 프로젝트가 어디에 있는지"를 파악할 수 있게 하는 것.** 전체 `docs/`를 다 읽지 않고도 현재 상태, 막힌 것, 다음 행동, 열려있는 질문을 한눈에 보게 한다.

## 왜 이 폴더가 필요한가 (실패 사례에서 배운 것)

실제 엔터프라이즈 프로젝트에서 관찰된 실패 패턴: "Live Tracker"라는 이름의 상태 문서 하나가 매 세션마다 "마지막 갱신" 배너를 위에 계속 추가하며 자라, 결국 실제 상태표(표 형태)에 도달하기도 전에 수백 줄의 세션 로그 벽을 읽어야 하는 문서가 되어버렸다. 원래 "덮어쓰기가 정상"이라고 설계했던 문서가 실제로는 append-only 로그로 변질된 것이다. 이 폴더는 그 실패를 구조적으로 막기 위해 존재한다.

## 하위 구조

| 파일 | 역할 | 갱신 방식 |
|---|---|---|
| [project-dashboard.md](project-dashboard.md) | 현재 페이즈, 건강도, 막힌 것, 다음 행동 — 압축 요약 | **덮어쓰기 전용.** 절대 append 금지 |
| [doc-governance-policy.md](doc-governance-policy.md) | 폴더별 문서 관리 규칙 (append-only/덮어쓰기/보관 정책, 크기 예산, 검토 주기, 오너십) | 정책 자체가 바뀔 때만 갱신 (드묾) |
| [open-questions.md](open-questions.md) | 사용자 결정을 기다리는 미해결 질문 목록 | 짧게 유지 — 해결되면 즉시 제거하고 답은 [07-decisions](../07-decisions/README.md) 또는 [10-consulting](../10-consulting/README.md)로 이동 |
| [external-reference-survey.md](external-reference-survey.md) | 이 하네스 설계 근거를 뒷받침하는 외부 레퍼런스 조사(업계 표준, 공식 가이드, 경쟁 프로젝트) 원문 요약 | 재조사할 때만 덮어쓰기 (예외적으로 원본 자료 — 규칙 1의 "요약/링크만" 대상이 아님) |

## 핵심 규칙 (예외 없음)

1. **이 폴더는 새로운 사실을 만들지 않는다** (단, [external-reference-survey.md](external-reference-survey.md)는 외부 조사 원본이므로 예외). 그 외 모든 내용은 [02-scenario](../02-scenario/README.md), [03-plan](../03-plan/README.md), [06-history](../06-history/README.md), [07-decisions](../07-decisions/README.md), [11-audit](../11-audit/README.md) 등 원본 문서의 요약/링크일 뿐이다. 원본과 이 폴더가 어긋나면 원본이 항상 맞다.
2. **`project-dashboard.md`는 크기 예산을 넘지 않는다** (권장: 150줄 이하). 예산을 넘기게 되는 갱신이라면, 오래된 항목을 지우지 말고 [06-history](../06-history/README.md) 또는 [11-audit/02-audit-closure-log](../11-audit/02-audit-closure-log/README.md)로 옮긴 뒤 대시보드에는 링크 한 줄만 남긴다.
3. **의미 없는 중간보고를 남기지 않는다.** "오늘 무엇을 확인했다" 같은 서술이 아니라 "지금 상태가 무엇인가"만 남긴다.
4. 이 원칙 자체를 어겼는지 판단이 애매하면 [doc-governance-policy.md](doc-governance-policy.md)의 폴더별 규칙표를 먼저 확인한다.

## 사람이 검토하는 방법 (권장 루틴)

- **매 페이즈 시작 전**: `project-dashboard.md` + `open-questions.md`만 읽는다 (2분).
- **의사결정이 필요할 때**: `open-questions.md`에서 대기 중인 항목을 확인하고 답한다.
- **정기 점검(주간/격주)**: `project-dashboard.md`의 "다음 감사 예정일"을 확인하고 [11-audit](../11-audit/README.md) 결과를 검토한다.
- **전체 문서가 방대해 어디서부터 봐야 할지 모를 때**: 이 폴더가 항상 출발점이다. 여기서 링크를 타고 필요한 원본으로만 이동한다.
