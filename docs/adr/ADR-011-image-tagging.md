# ADR 011 – 이미지 태깅 전략

## Context
이미지 태그는 추적성과 가독성을 동시에 고려해야 한다.  
sha7, 날짜/시간, PR 번호 등 다양한 방식이 있다.

## Decision
태그 포맷은 **`MMDD_HHMM_<branch>`** 형식으로 한다.  
예시:
- feature 브랜치: `0821_1045_feature5`  
- issue 브랜치: `0821_1045_issue2`  
- main: `0821_1045_main`

## Status
Accepted

## Consequences
- 사람이 보기에 직관적이다.  
- Actions 로그와 연결해 어떤 커밋에서 빌드됐는지 추적 가능하다.  
- sha7 태그는 초기에는 제외했지만, 필요시 보조 태그로 추가 가능하다.
