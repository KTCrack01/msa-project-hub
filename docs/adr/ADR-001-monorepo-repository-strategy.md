# ADR-001: Monorepo Repository Strategy

## Status
Accepted

## Context
여러 서비스를 하나의 저장소에 두는 모노레포 구조를 사용하고 있다. 공통 규칙과 파이프라인 전략을 정의할 필요가 있다.

## Decision
- 루트에 서비스별 디렉터리(`api-*-svc`, `web-frontend`, `msa-project-hub`)를 두는 모노레포 유지
- 서비스 디렉터리 변경 감지 기반 CI/CD(경로 필터)로 부분 빌드/배포
- 공통 규칙과 ADR/문서는 `msa-project-hub`에서 관리
- 브랜치/릴리스 전략은 ADR-011, 이미지 태깅은 ADR-012 준수

## Consequences
- 👍 변경 범위에 따라 필요한 서비스만 빌드/배포해 속도 향상
- 👍 공통 문서와 규칙을 중앙에서 관리
- 👎 저장소가 비대해질 수 있어 경로 기반 파이프라인 관리가 필수


