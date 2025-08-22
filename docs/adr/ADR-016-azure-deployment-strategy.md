# ADR-016: Azure Deployment Strategy

## Status
Accepted

## Context
MSA를 Azure에 배포할 때, 초기에는 단순성이 중요.

## Decision
1단계: Azure App Service  
2단계: 필요시 Azure Container Apps(ACA)  
3단계: 고도화 시 AKS(Kubernetes)  

## Consequences
- 👍 점진적 학습 및 비용 관리 가능
- 👎 서비스 확장시 단계별 마이그레이션 필요
