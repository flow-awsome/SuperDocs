# 10-consulting — 지속 컨설팅

프로젝트 착수 시 1회만 진행하는 최초 인터뷰는 [mastery/00-initial-intake](../../mastery/00-initial-intake/README.md)에서 다룬다. 이 폴더는 프로젝트가 진행되는 **내내 반복되는** 개발자-AI-사용자 간의 소통 공간이다 — 페이즈가 바뀔 때마다, 결정이 필요할 때마다, 아이디어가 떠오를 때마다 계속 쓰인다.

## 하위 구조

| 폴더 | 시점 | 내용 |
|---|---|---|
| [01-phase-consulting](01-phase-consulting/README.md) | 각 페이즈 시작/종료 시 | 페이즈 단위 컨설팅 세션 — 방향 재확인, 스코프 조정 |
| [02-decision-interviews](02-decision-interviews/README.md) | 의사결정 필요 시점 | 선택지형 질의응답 (A/B 트레이드오프 등) |
| [03-discussion-log](03-discussion-log/README.md) | 상시 | 자유 토론, 아이디어, 아직 구조화되지 않은 논의 |

## mastery와의 관계

[mastery](../../mastery/README.md)는 프로젝트를 시작하기 **전** 다운로드해서 한 번 채우는 설정 인터뷰다. 이 폴더는 프로젝트가 시작된 **후** 계속 쌓이는 운영 컨설팅이다. mastery의 인터뷰 결과가 이 프로젝트의 `docs/` 초기 뼈대를 만들었다면, 이 폴더는 그 뼈대가 실제로 살아 움직이는 동안의 대화 기록이다.

## 사용 원칙

- AI는 애매한 비즈니스 의도를 **추측으로 채우지 않는다.** 이 폴더에 질문을 만들어 남기거나, 대화 중 직접 사용자에게 확인한다.
- 컨설팅 결과 확정된 사항은 반드시 관련 [07-decisions](../07-decisions/README.md) 또는 [02-scenario](../02-scenario/README.md) 문서로 승격(promote)한다. 컨설팅 폴더 자체를 "최종 스펙"으로 취급하지 않는다.
- 하나의 질문지/세션은 하나의 파일로 유지한다 (여러 세션을 한 파일에 누적하지 않는다) — 검색성과 토큰 효율을 위해. 예외는 [03-discussion-log](03-discussion-log/README.md) (주제별 누적 허용).
