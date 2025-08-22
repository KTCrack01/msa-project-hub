# ADR-014: Container Build and Runtime Policy

## Status
Accepted

## Context
각 서비스의 Docker 이미지 빌드/런타임 표준을 통일해 보안성과 재현성을 확보한다.

## Decision
- 멀티 스테이지 Docker 빌드 사용(Gradle 이미지로 빌드, 경량 JRE로 런타임)
- 런타임 베이스: `eclipse-temurin:21-jre`
- 컨테이너는 비루트 사용자로 실행(`spring` 시스템 사용자/그룹)
- 기본 노출 포트: 8080 (ADR-004와 일관)
- JAR 실행 진입점: `ENTRYPOINT ["java", "-jar", "app.jar"]`
- 의존성 캐시 최적화를 위해 `build.gradle`, `settings.gradle`, `gradle/`를 먼저 복사
- 빌드 시 테스트는 파이프라인에서 수행하고 이미지 빌드는 `-x test` 허용 가능

## Consequences
- 👍 이미지 크기와 빌드 시간이 최적화된다.
- 👍 기본 보안 태세(비루트 사용자)가 강화된다.
- 👎 빌드와 런타임 베이스 이미지 관리가 필요하다.


