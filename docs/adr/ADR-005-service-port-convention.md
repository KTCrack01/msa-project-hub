# ADR-004: Service Port Convention

## Status
Accepted

## Context
서비스별 포트가 제각각이면 관리 어려움.

## Decision
Frontend 컨테이너는 `3000`, Backend 서비스들은 `8080`으로 통일.

## Consequences
- 👍 운영/문서화 용이
- 👎 일부 서비스 포트 충돌 가능성 (추후 조정 필요)
