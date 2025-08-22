# ADR-020: Monitoring Strategy

## Context
공인알림문자 서비스의 운영 모니터링을 위해 Azure의 모니터링 솔루션 선택이 필요했다.  

**초기 계획**:
- Application Insights (APM)
- Log Analytics Workspace  
- Azure Key Vault
- 통합 모니터링 대시보드

**실제 제약사항**:
- Application Insights 리소스 생성 실패 (`ResourceGroupNotFound`)
- Log Analytics 생성 권한 제한
- 시간 제약으로 인한 고급 기능 구현 지연

## Decision
**제한된 환경에서 활용 가능한 최소 모니터링 전략 채택**

**실제 구현된 모니터링**:
- **Azure Monitor 기본 메트릭**: App Service에서 자동 제공
- **Spring Boot Actuator**: `/actuator/health` 헬스체크
- **Manual Health Check**: 각 서비스 URL 수동 확인
- **GitHub Actions 로그**: CI/CD 파이프라인 모니터링

## Status
Accepted

## Consequences

### 👍 **긍정적 효과**
- **현실적 대안**: 제한된 환경에서도 최소 모니터링 구현
- **즉시 활용**: 추가 권한 요청 없이 바로 사용 가능
- **기본 가시성**: Azure Monitor를 통한 서비스 상태 확인
- **헬스체크 구현**: Spring Boot Actuator로 서비스 생존 여부 확인
- **학습 경험**: 교육 환경의 제약 조건 하에서 문제 해결 경험

### 👎 **제한사항**
- **모니터링 깊이 부족**: Application Insights 없이 상세 APM 불가
- **중앙 집중 로깅 미구현**: 각 서비스 로그가 분산되어 있음
- **알림 체계 부재**: 장애 발생 시 자동 알림 불가
- **커스텀 메트릭 부족**: 비즈니스 메트릭 수집 미구현
- **보안 관리 미흡**: Azure Key Vault 미구현으로 시크릿 관리 취약점 존재

### 📚 **학습 포인트**
- **제약 조건 관리**: 실제 프로젝트에서 직면하는 환경적 제약 극복
- **우선순위 조정**: 핵심 기능 구현에 집중, 부가 기능은 차순위
- **대안 모색**: 이상적 설계와 현실적 구현 사이의 균형점 찾기

## Lessons Learned
1. **교육 환경 특성 이해**: Azure 리소스 권한 제한 사전 파악 필요
2. **단계적 구현**: MVP 완성 후 점진적 기능 확장이 더 안전
3. **문서화 중요성**: 제약사항과 대안책을 명확히 기록하여 의사결정 과정 투명화

## Future Roadmap
**실제 운영 환경 이전 시 구현 예정**:
- Application Insights 도입으로 상세 APM 구현
- Log Analytics Workspace를 통한 중앙 집중 로깅
- Azure Key Vault를 통한 보안 강화
- Custom Dashboard 구축으로 비즈니스 메트릭 시각화