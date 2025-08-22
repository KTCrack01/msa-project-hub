# ADR-015: API Versioning and Base Path Convention

## Status
Accepted

## Context
여러 서비스가 프런트엔드와 통신하며, 장기적으로 API 변경을 관리해야 한다. 현재 `api-login-svc` 등에서 `/api/v1/...` 경로를 사용 중이다.

## Decision
- 베이스 경로는 `/api/v1`로 통일한다.
- 파생 서비스는 도메인 하위 경로를 사용한다(예: `/api/v1/users`, `/api/v1/messages`, `/api/v1/contacts`).
- 하위 호환이 불가한 변경은 `v2` 등 새 버전으로 추가하며, 구버전은 일정 기간 유지 후 폐기한다.

## Consequences
- 👍 프런트엔드/문서화에서 경로 규칙이 명확해진다.
- 👍 파괴적 변경 시 버전 공존이 가능하다.
- 👎 다중 버전 유지 관리 비용이 발생한다.


