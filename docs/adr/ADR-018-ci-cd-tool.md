# ADR 018 – CI/CD 파이프라인 툴 선택

## Context
공인알림문자 서비스는 MSA(6개 서비스) 구조이며 GitHub을 코드 저장소로 사용한다.  
빌드/배포 자동화를 위해 CI/CD 도구가 필요하다.

## Decision
**GitHub Actions**를 CI/CD 엔진으로 사용한다.

## Status
Accepted

## Consequences
- GitHub과 코드 저장소가 동일 플랫폼이라 설정이 단순하다.  
- Marketplace 액션을 활용해 Azure App Service 및 Docker Hub와 연동이 쉽다.  
- Jenkins 등 외부 툴에 비해 진입장벽이 낮다.  
- 추후 확장 시 self-hosted runner나 다른 도구로 이전 고려 가능.
