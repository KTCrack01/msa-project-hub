# ADR 010 – 브랜치 전략

## Context
현재 브랜치는 `main`, `feature/*`, `issue/*` 세 가지 패턴만 사용한다.  
코드 리뷰와 테스트를 보장하고, main은 배포용으로만 쓴다.

## Decision
- `feature/*`, `issue/*`: 빌드 및 테스트만 실행  
- `main`: 머지 후 이미지 빌드 & Docker Hub 푸시 & App Service 재배포

## Status
Accepted

## Consequences
- 단순하고 직관적인 워크플로우 유지  
- QA 환경이 따로 없으므로 main 머지 = 운영 배포  
- 브랜치 보호 규칙으로 main 직접 푸시는 차단해야 함
