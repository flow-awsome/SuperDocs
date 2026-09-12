# 02-user-flows — 사용자 흐름

사용자 여정과 화면 단위 흐름을 담는다. [01-feature-scenarios](../01-feature-scenarios/README.md)가 기능 단위라면, 여기는 사용자 관점의 end-to-end 흐름이다. Next.js 화면 구성과 직접 연결된다.

**이 폴더는 "구현 여부와 무관하게, 이 서비스가 제공해야 할 흐름 전체 목록"이다.** 아직 코드로 없어도 여기 먼저 흐름을 등록한다 — 신규 기능 구상이나 제3자 관점 검토를 할 때, 구현된 것만 보고는 전체 그림을 볼 수 없기 때문이다. 구현되면 흐름 자체를 지우지 않고 상태만 갱신한다.

## 파일

- [flow-catalog.md](flow-catalog.md) — 전체 흐름을 한눈에 보는 마스터 인덱스 (역할 × 상태로 정렬). **이 폴더에 들어올 때 항상 여기부터 본다.**
- `flow-<슬러그>.md` — 흐름별 상세 (템플릿: [_template-user-flow.md](_template-user-flow.md))
- `diagrams/` (선택) — 다이어그램 도구(Excalidraw 등)로 그린 원본+렌더 이미지. mermaid로 충분하면 이 폴더 없이 흐름 파일 안에 mermaid만 써도 된다 — 화면 배치/분기가 mermaid로 표현하기 버거울 만큼 복잡할 때만 별도 다이어그램 도구를 쓴다.

## 파일명 규칙

`flow-<슬러그>.md`

## 상태 값 (flow-catalog.md와 각 흐름 파일 공통)

| 상태 | 의미 |
|---|---|
| 목록화됨 | 있어야 할 흐름으로 등록만 됨, 상세 미작성 |
| 상세작성됨 | 단계별 표까지 채워짐, 미구현 |
| 구현됨 | 실제 코드로 존재 — [04-code](../../04-code/README.md)의 대응 문서로 링크 필수 |
| 변경검토중 | 구현된 흐름인데 요구사항이 바뀌어 재검토 중 |

## 연결 지점

- UI 검증: [05-test/04-ui-verification](../../05-test/04-ui-verification/README.md)
- Next.js 라우트 매핑: [01-architecture/01-system-composition/module-composition-map.md](../../01-architecture/01-system-composition/module-composition-map.md)
- 구현된 흐름의 실제 코드 위치: [04-code/01-business-logic](../../04-code/01-business-logic/README.md)
