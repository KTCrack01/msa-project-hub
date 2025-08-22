# ADR-002: Authentication Strategy

## Status
Deferred

## Context
OAuth2, JWT 등 인증/인가 방식을 도입하려 했으나 MSA 환경에서 관리 복잡성이 큼.

## Decision
로그인 서비스 인증 고도화(OAuth2, 카카오 로그인 등)는 추후로 미루고, 현재는 단순 사용자 관리로 진행.

## Consequences
- 👍 개발 초기 복잡도 낮춤
- 👎 보안/확장성은 한계 존재
