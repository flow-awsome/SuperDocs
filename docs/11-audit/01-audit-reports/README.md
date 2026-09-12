# 01-audit-reports — 감사 리포트

[00-audit-charters](../00-audit-charters/README.md)에 정의된 렌즈로 실제 감사를 수행한 결과. append-only — 과거 리포트를 수정하지 않는다.

## 파일명 규칙

`YYYY-MM-DD-<라운드슬러그>.md`

## 템플릿

[_template-audit-report.md](_template-audit-report.md)

## 작성 원칙

- 발견 사항마다 근거(파일:라인 또는 문서 링크)를 반드시 포함한다 — 사람이 재현/재검증할 수 있어야 한다.
- 심각도 태그(🔴/🟠/🟡)는 [00-audit-charters](../00-audit-charters/README.md)의 판정 기준을 따른다.
- 이 라운드에서 고친 항목이 있어도 "완료"로 단정하지 않는다 — [02-audit-closure-log](../02-audit-closure-log/README.md)에서 다음 라운드 재검증 대상으로 등록한다.
