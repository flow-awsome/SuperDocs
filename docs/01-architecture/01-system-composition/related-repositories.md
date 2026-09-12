# 관련 저장소 레지스트리

이 프로젝트가 다른 Git 저장소와 함께 하나의 시스템을 이루는 멀티레포 구성일 때만 존재하는 문서다 ([mastery/00-initial-intake/05-related-projects.md](../../../mastery/00-initial-intake/05-related-projects.md)에서 확정). 해당 없으면 이 파일 자체를 만들지 않는다.

**이 문서의 역할은 "매번 다른 저장소를 통째로 읽게 하는 것"이 아니라, 경계에 걸친 작업이 실제로 생겼을 때 어디를 봐야 하는지 최소한의 좌표만 남기는 것이다** — [00-control-tower/doc-governance-policy.md](../../00-control-tower/doc-governance-policy.md)의 JIT(필요시 로드) 원칙을 저장소 경계 너머로 확장한 것.

## 레지스트리

| 저장소명 | 역할 | Git URL | 관계 | 접근 방법 | 조사 시 우선 참조 문서 |
|---|---|---|---|---|---|
| | | | 소비/제공/양방향 | public(WebFetch) / private-같은조직(`gh`) / private-접근불가(사용자에게 확인) | [service-boundary-map](), [02-api-contracts](), [07-decisions/01-architecture-decisions]() |

"조사 시 우선 참조 문서" 칸은 그 저장소의 실제 파일로 가는 링크(raw/blob URL)여야 한다 — 저장소 이름만 적어두고 실제 경로를 안 채우면 이 문서는 무용지물이다.

## 이 저장소로부터 다른 저장소에 영향을 주는 최근 결정 (최대 5개)

[project-dashboard.md](../../00-control-tower/project-dashboard.md)의 "최근 확정된 중대 결정"과 동일한 방식 — 덮어쓰기, 5개 넘으면 오래된 것부터 제거(전체 기록은 [07-decisions](../../07-decisions/README.md) 원문에 남아있으므로 삭제해도 유실 아님).

| 일자 | 이 저장소의 결정 | 영향받는 저장소 | ADR 링크 |
|---|---|---|---|
| | | | |

## 조사 원칙

1. **경계에 걸친 작업(공유 계약 변경, 인증 방식 변경, 인터페이스 추가/제거)을 할 때만** 위 레지스트리에서 관련 저장소를 찾아 "조사 시 우선 참조 문서" 링크만 그때그때 확인한다. 관련 없는 작업에서는 이 문서를 열지 않아도 된다.
2. **접근 방법에 따라**:
   - public → `WebFetch`로 raw 파일을 바로 읽는다.
   - private(같은 조직) → `gh api repos/<org>/<repo>/contents/<path>` 등으로 조회한다.
   - private(접근 불가) → 추측하지 않는다. 사용자에게 현재 값을 직접 물어보거나 [00-control-tower/open-questions.md](../../00-control-tower/open-questions.md)에 등록한다.
3. **다른 저장소도 이 하네스(SuperDocs)를 쓰고 있다면** "조사 시 우선 참조 문서"는 그 저장소의 동일한 상대 경로([01-system-composition/service-boundary-map.md](service-boundary-map.md), [04-code/02-api-contracts](../../04-code/02-api-contracts/README.md), [07-decisions](../../07-decisions/README.md))로 예측 가능하다. 아니라면 그 저장소의 실제 문서 구조에 맞는 링크를 받아서 채운다.
4. **이 저장소에서 다른 저장소에 영향을 주는 결정을 내렸다면**: 평소처럼 [07-decisions](../../07-decisions/README.md)에 ADR을 남기고, 위 "최근 결정" 표에도 한 줄 추가한다 — 다른 저장소의 에이전트가 이 표만 보고 "여기 뭔가 바뀌었다"를 알아챌 수 있게 하는 것이 유일한 목적이다. ADR을 쓰는 것만으로는 다른 저장소에 전파되지 않는다.
5. 다른 저장소가 이 표를 통해 확인한 결정에 대응해 자기 쪽 작업을 했다면, 그 사실을 자기 저장소의 [06-history](../../06-history/README.md)에 남긴다 — "왜 그 변경을 했는가"의 출처가 다른 저장소의 ADR임을 명시한다.

## 갱신 시점

관련 저장소가 추가/제거되거나 접근 방법이 바뀔 때 레지스트리를 갱신한다. "최근 결정" 표는 관련 저장소에 영향 주는 결정이 생길 때마다 갱신한다.
