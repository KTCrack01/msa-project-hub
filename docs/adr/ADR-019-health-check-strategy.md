# ADR-013: Health Check Strategy

## Context
MSA 환경에서 각 서비스의 상태 모니터링을 위한 헬스체크 전략이 필요했다.  
Spring Boot Actuator의 기본 헬스체크와 비즈니스 로직에 특화된 커스텀 헬스체크 중 선택해야 했다.

초기에는 api-aiagent-svc에 OpenAI API 연결 상태를 확인하는 커스텀 헬스체크를 구현하려 했으나,  
WebClient 의존성 관련 컴파일 에러가 발생하여 CI/CD 파이프라인이 실패했다.

## Decision
**모든 서비스에 Spring Boot Actuator 기본 헬스체크(`/actuator/health`)만 적용한다.**

- 모든 Backend 서비스(5개)에 `spring-boot-starter-actuator` 의존성 추가
- `management.endpoints.web.exposure.include=health,info` 설정 통일
- 커스텀 헬스체크는 향후 안정성 확보 후 추가 고려

## Status
Accepted

## Consequences
- 👍 **일관성**: 모든 서비스가 동일한 헬스체크 경로 사용
- 👍 **안정성**: 검증된 Spring Boot Actuator 기능으로 빌드 실패 위험 제거
- 👍 **Azure 호환성**: App Service에서 `/actuator/health` 엔드포인트 활용 가능
- 👍 **자동 확장**: 데이터베이스, 디스크 공간 등 기본 헬스체크 항목 포함
- 👎 **세부 모니터링 부족**: 외부 API(OpenAI, Twilio) 상태는 별도 확인 필요
- 👎 **비즈니스 로직 미반영**: 서비스별 특화된 상태 확인 불가

## Future Considerations
- 안정화 후 단계적으로 커스텀 헬스체크 추가
- 외부 API 의존성 모니터링을 위한 별도 메트릭 수집 검토