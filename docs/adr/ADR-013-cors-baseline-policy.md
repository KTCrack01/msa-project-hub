# ADR-013: CORS Baseline Policy

## Status
Accepted

## Context
프런트엔드(`web-frontend`)에서 각 백엔드 서비스를 호출한다. 로컬 개발과 배포 환경에서의 CORS 정책을 통일해 예측 가능성을 높인다. 일부 서비스에서 `http://localhost:3000`을 허용 중이다.

## Decision
- 로컬: `http://localhost:3000` 및 개발 프론트엔드 도메인 허용
- 운영: 배포된 프론트엔드 도메인만 허용, 크리덴셜/메서드/헤더는 최소 허용 원칙
- 환경 변수/설정으로 도메인 목록 주입 가능

## Consequences
- 👍 환경별 동작이 예측 가능하고 보안성 향상
- 👎 도메인 변경 시 설정 변경/배포가 필요


