# 00-business-logic-changelog — 비즈니스 로직 변경 로그

도메인 규칙, API 계약, 데이터 스키마 등 비즈니스 로직에 영향을 주는 변경을 기록한다.

## 파일명 규칙

`YYYY-MM-changelog.md` (월별 누적)

## 항목 형식

```
## YYYY-MM-DD — (변경 제목)
- 변경 전:
- 변경 후:
- 영향 범위: (관련 04-code, 02-scenario 링크)
- 근거: [07-decisions](../../07-decisions/README.md) 링크
```

## 작성 원칙

- 코드 diff의 요약이 아니라 **의미 있는 변화**만 남긴다 (오타 수정 등은 제외).
- Breaking Change는 반드시 근거 결정 링크를 포함한다.
