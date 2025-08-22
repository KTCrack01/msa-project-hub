# ADR-013: Technology Stack Baseline

## Status
Accepted

## Context
모든 백엔드 서비스가 공통적으로 사용하는 기술 스택과 최소 버전을 명확히 하여 빌드/런타임 일관성, 보안 업데이트, 운영 표준을 맞춘다.

## Decision
- 언어/런타임: Java 21 (Temurin)
- 프레임워크: Spring Boot 3.5.4
- 빌드: Gradle 8.x, Spring Dependency Management 1.1.7
- 데이터 액세스: Spring Data JPA (+ PostgreSQL 드라이버)
- 검증: `spring-boot-starter-validation` (필요 서비스 적용)
- 문서화: springdoc-openapi (적용 가능한 서비스)
- 공통 라이브러리: Lombok (compileOnly + annotationProcessor)

## Consequences
- 👍 서비스 간 호환성과 보안 패치 관리가 용이하다.
- 👍 공통 템플릿으로 신규 서비스 부팅이 빨라진다.
- 👎 하위 호환성이 떨어지는 경우(예: Java 17) 마이그레이션 비용이 발생한다.


