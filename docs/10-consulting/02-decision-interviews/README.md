# 02-decision-interviews — 결정 인터뷰

특정 트레이드오프에서 선택이 필요할 때, AI가 사용자에게 **선택지 형태로 좁혀서** 질문하고 답변을 기록하는 공간이다. 열린 토론은 [03-discussion-log](../03-discussion-log/README.md)에, 이미 좁혀진 갈림길 선택은 여기에 남긴다.

## 언제 쓰는가

- 두 개 이상의 구현/아키텍처 옵션 중 하나를 선택해야 할 때
- 완결성 vs 비용, 속도 vs 품질처럼 트레이드오프가 명확한 결정
- 사용자의 취향/우선순위 확인이 필요한 결정 (기술적으로는 둘 다 가능하지만 방향성이 다른 경우)

## 파일명 규칙

`decision-<주제-슬러그>-<YYYY-MM-DD>.md`

## 템플릿

[_template-decision-interview.md](_template-decision-interview.md)

## 결과 반영처

인터뷰 결과 확정된 선택은 반드시 [07-decisions](../../07-decisions/README.md)에 ADR로 승격한다. 이 폴더의 문서는 "질문 과정"의 기록이고, ADR은 "확정된 결론"의 기록이다.
