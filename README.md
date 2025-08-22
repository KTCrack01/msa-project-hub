# 📡 공인알림문자 서비스 — MSA Project Hub

> 공공 및 민간 기관의 대량 알림(SMS)을 편리하게 전송하고,  
> **통계 시각화·AI Agent 지원**까지 제공하는 MSA 학습/실전 프로젝트입니다.

---

## 📌 기본 정보

- **팀명**: 🚀 1조

### 👥 담당자 & 서비스

| 담당자     | 담당 서비스                          |
|------------|-------------------------------------|
| **김지우** | 전화번호부, 로그인                   |
| **이성무** | 프론트엔드, AI Agent, 메시지 보내기 |
| **강수민** | 메시지 보내기, 메시지 대시보드       |

---

### 🌐 데모 링크

| 구분 | URL |
|------|-----|
| **프로덕트** | https://web-frontend-ffasfgacfyceeagj.koreacentral-01.azurewebsites.net |
| **프론트엔드** | https://web-frontend-ffasfgacfyceeagj.koreacentral-01.azurewebsites.net |
| **로그인** | https://login-svc-gbg8ephsd6bufnca.koreacentral-01.azurewebsites.net |
| **메시지 보내기** | https://messaging-svc-a0euekhwgueqd7c0.koreacentral-01.azurewebsites.net |
| **메시지 대시보드** | https://analytics-svc-aucrheemh4edbtac.koreacentral-01.azurewebsites.net |
| **전화번호부** | https://phonebook-svc-dtd4f8f9cyfee5c0.koreacentral-01.azurewebsites.net |
| **AI Agent 메시지 보내기** | https://aiagent-svc-dka3epddc7f5hdbm.koreacentral-01.azurewebsites.net |

---

### 🏷️ 릴리즈 정보
- **버전**: `v1.0`  
- **날짜**: `2025-08-21`

---

### ✨ 주요 기능
- 📩 메시지 전송  
- 📜 메시지 기록 저장  
- 🤖 AI Agent 지원  
- 📊 메시지 대시보드 (전송량, 성공률 등)  
- 📞 전화번호부 관리  

---

### 🌟 프로젝트 특장점
**📊 실시간 대시보드 제공**
- 문자 서버와 연동해 데이터를 실시간 업데이트
- [근거](https://eight-store-0c3.notion.site/256d8432636380889e17f72c60c1cb8f?source=copy_link)

**🧩 MSA 기반 독립 배포**
- 마이크로서비스 아키텍처(MSA) 설계로 서비스별 독립 배포·운영 가능
- 특정 서비스 장애 발생 시에도 전체 서비스는 정상 동작
- 시스템 확장성 & 안정성 강화
- [근거](https://eight-store-0c3.notion.site/MSA-256d8432636380c3803be764a82e3809?source=copy_link)

---

## 🏗️ 시스템 아키텍처

### 기술 스택
- **Back-end**: Spring Boot  
- **Front-end**: React  
- **Infra**: Azure (App Service → ACA → AKS 고도화)  
- **DB**: Azure DB for PostgreSQL (서비스별 DB 분리)  
- **Secret 관리**: `.env`(로컬), Azure App Service 환경변수 & Key Vault  

### 포트 정책
- Frontend: `3000`  
- Backend 서비스들: `8080`  

### 🏗️ System Architecture
![Architecture](docs/images/arch_mermaid.png)
> **상세 아키텍처 문서**: [📐 Architecture Guide](docs/architecture.md)

### 핵심 플로우
문자 메시지 과정
<img width="718" height="400" alt="Image" src="https://github.com/user-attachments/assets/e59ef450-d72f-46d8-a26f-8385b7980ab6" />

### ERD
<img width="960" height="642" alt="Image" src="https://github.com/user-attachments/assets/9e667d47-a92a-4fad-8155-8410af09cbb0" />

### 시연 영상
https://www.youtube.com/watch?v=vbTuP_6fmOU

### 코드 품질 보증
CI/CD 진행
<img width="1052" height="781" alt="Image" src="https://github.com/user-attachments/assets/d68dc01a-b6a4-497c-b5a6-001f6958cb9a" />

### 협업 과정 기록
<img width="1138" height="876" alt="Image" src="https://github.com/user-attachments/assets/1a9e9b60-050c-44e9-bf1a-3e7accb05fe7" />
<img width="721" height="739" alt="Image" src="https://github.com/user-attachments/assets/fd93688e-64e3-4840-ab7d-e099eb650c46" />
---

## 🥇 팀원별 개인 회고

### 강수민
- MSA 구조를 이해할 수 있는 상황이었다. 변경에도 전체 기능에 영향이 적어 큰 서비스에서 왜 사용하는지 알 것 같다.    
- 기능 개수에만 집중해서, 처음에는 기능을 개발하는데만 집중했는데, 무엇이 불편한지 문제를 찾고 이를 해결하는 것이 중요하다는 것을 막바지에 깨달았다. 우리는 엔지니어임을 잊지말자!

### 김지우
- 클라우드 기반 MSA 개발을 하며 설계 단계부터 고려할 부분이 많다는 것을 느꼈다. 특히 클라우드 환경의 라우팅과 설정 충돌 문제를 경험하며 아키텍처 설계의 중요성을 알게 되었다.
- 또한 CI/CD를 처음 적용하면서, 수동 배포의 비효율성을 체감했고 자동화의 필요성과 장점을 명확히 이해할 수 있었다. 개발적인 부분에서 부족함도 느꼈지만, 클라우드와 인프라 경험은 흥미로웠으며, 앞으로의 직무 진로를 더 구체화하는 계기가 되었다.

### 이성무
- 이번 프로젝트에서는 프론트엔드와 백엔드 개발을 처음 맡아 진행하면서 어려움이 많았지만, 그 과정을 통해 개발 전반의 프로세스를 조금이나마 이해할 수 있어 의미가 있었다.
- 특히, 시간에 쫓기며 기획이 충분히 이루어지지 않은 상태에서 개발을 진행하다 보니 여러 어려움이 발생했는데, 이를 통해 앞으로는 기획 단계에서부터 보다 정밀한 계획을 세우는 것이 중요하다는 점을 깨달았다.
- 또한, Docker, Azure, CI/CD를 활용하여 자동화된 개발과 배포 과정을 직접 경험할 수 있어 많은 것을 배우고 성장할 수 있었던 프로젝트였다.
  
---

## 📦 서비스 레포지토리

| 서비스 | 설명 | DB |
|---|---|---|
| [`api-messaging-svc`](https://github.com/KTCrack01/api-messaging-svc) | 메시지 생성/전송, 수신자 기록, 상태 콜백 처리 | messaging-db |
| [`api-analytics-svc`](https://github.com/KTCrack01/api-analytics-svc) | 전송 로그 집계, 대시보드 API | analytics-db |
| [`api-phonebook-svc`](https://github.com/KTCrack01/api-phonebook-svc) | 전화번호부 CRUD, 단체 발송 대상 제공 | phonebook-db |
| [`api-login-svc`](https://github.com/KTCrack01/api-login-svc) | 사용자 로그인 관리 (OAuth2/JWT는 추후 고도화) | login-db |
| [`api-aiagent-svc`](https://github.com/KTCrack01/api-aiagent-svc) | OpenAI API 백엔드 프록시 (Key Vault 관리) | - |
| [`web-frontend`](https://github.com/KTCrack01/web-frontend) | React 기반 UI (Dashboard, Messaging, Phonebook, AI) | - |

> 전체 목록: [KTCrack01 · Repositories](https://github.com/orgs/KTCrack01/repositories)

---

## 📋 프로젝트 현황

> **전체 개발 현황 및 완성도 추적**: [📊 Project Board](docs/project-board.md)  
> **프로젝트 결과보고 및 회고**: [🎯 Project Retrospective](docs/project-retrospective.md)  
> **보안 분석 및 고도화 방안**: [🔒 Security Enhancement](docs/security-analysis-and-enhancement.md)

**현재 상태**: 🎯 **95% Complete** | 🟢 **Production Ready**

---

## 📚 기술 문서

### **🏗️ 아키텍처 & 설계**
- **[📐 System Architecture](docs/architecture.md)** - 전체 시스템 아키텍처 다이어그램 및 상세 설명
- **[🚀 Deployment Guide](docs/3_deployment.md)** - 배포 가이드 및 운영 매뉴얼

### **🔒 보안 & 모니터링**  
- **[🔒 Security Analysis](docs/security-analysis-and-enhancement.md)** - 보안 취약점 분석 및 고도화 방안
- **[🎯 Project Retrospective](docs/project-retrospective.md)** - 프로젝트 회고 및 학습 성과

---

## 📚 Architecture Decision Records (ADR)

허브 내 `docs/adr/` 경로에 기록  

| 번호 | 제목 | 상태 | 링크 |
|------|------|------|------|
| ADR-001 | Monorepo Repository Strategy | Accepted | [ADR-001](docs/adr/ADR-001-monorepo-repository-strategy.md) |
| ADR-002 | Technology Stack Baseline | Accepted | [ADR-002](docs/adr/ADR-002-technology-stack-baseline.md) |
| ADR-003 | API Versioning and Base Path | Accepted | [ADR-003](docs/adr/ADR-003-api-versioning-and-base-path.md) |
| ADR-004 | Database Per Service | Accepted | [ADR-004](docs/adr/ADR-004-database-per-service.md) |
| ADR-005 | Service Port Convention | Accepted | [ADR-005](docs/adr/ADR-005-service-port-convention.md) |
| ADR-006 | Authentication Strategy | Accepted | [ADR-006](docs/adr/ADR-006-authentication-strategy.md) |
| ADR-007 | SMS Provider Selection | Accepted | [ADR-007](docs/adr/ADR-007-sms-provider-selection.md) |
| ADR-008 | Messaging AI History | Accepted | [ADR-008](docs/adr/ADR-008-messaging-ai-history.md) |
| ADR-009 | OpenAI API Integration | Accepted | [ADR-009](docs/adr/ADR-009-openai-api-integration.md) |
| ADR-010 | Branch Strategy | Accepted | [ADR-010](docs/adr/ADR-010-branch-strategy.md) |
| ADR-011 | Image Tagging | Accepted | [ADR-011](docs/adr/ADR-011-image-tagging.md) |
| ADR-012 | Secret and Config Management | Accepted | [ADR-012](docs/adr/ADR-012-secret-and-config-management.md) |
| ADR-013 | CORS Baseline Policy | Accepted | [ADR-013](docs/adr/ADR-013-cors-baseline-policy.md) |
| ADR-014 | Container Build and Runtime Policy | Accepted | [ADR-014](docs/adr/ADR-014-container-build-and-runtime-policy.md) |
| ADR-015 | Phonebook Service Separation | Accepted | [ADR-015](docs/adr/ADR-015-phonebook-service-separation.md) |
| ADR-016 | Azure Deployment Strategy | Accepted | [ADR-016](docs/adr/ADR-016-azure-deployment-strategy.md) |
| ADR-017 | Dummy Data Usage | Accepted | [ADR-017](docs/adr/ADR-017-dummy-data-usage.md) |
| ADR-018 | CI/CD Tool | Accepted | [ADR-018](docs/adr/ADR-018-ci-cd-tool.md) |
| ADR-019 | Health Check Strategy | Accepted | [ADR-019](docs/adr/ADR-019-health-check-strategy.md) |
| ADR-020 | Monitoring Strategy | Accepted | [ADR-020](docs/adr/ADR-020-monitoring-strategy.md) |
| ADR-021 | OIDC Authentication Strategy | Accepted | [ADR-021](docs/adr/ADR-021-oidc-authentication-strategy.md) |

---

# 🏥 헬스체크 및 상태 모니터링

> **서비스 상태 실시간 확인**: 모든 마이크로서비스 헬스체크 엔드포인트 제공  
> **Spring Boot Actuator**: 표준화된 헬스체크 구현  
> **Azure App Service**: 자동 헬스체크 통합

---

## 1. 서비스별 헬스체크 엔드포인트

### 📋 **백엔드 서비스 헬스체크**

```bash
# 각 서비스 상태 확인
curl https://login-svc-gbg8ephsd6bufnca.koreacentral-01.azurewebsites.net/actuator/health      # 🔐 Login Service
curl https://messaging-svc-a0euekhwgueqd7c0.koreacentral-01.azurewebsites.net/actuator/health  # 📤 Messaging Service  
curl https://phonebook-svc-dtd4f8f9cyfee5c0.koreacentral-01.azurewebsites.net/actuator/health  # 📞 Phonebook Service
curl https://analytics-svc-aucrheemh4edbtac.koreacentral-01.azurewebsites.net/actuator/health  # 📊 Analytics Service
curl https://aiagent-svc-dka3epddc7f5hdbm.koreacentral-01.azurewebsites.net/actuator/health   # 🤖 AI Agent Service
```

### 🌐 **프론트엔드 헬스체크**

```bash
# 웹 프론트엔드 상태 확인  
curl https://web-frontend-ffasfgacfyceeagj.koreacentral-01.azurewebsites.net/                 # 🌐 Web Frontend
```

---

## 2. 헬스체크 응답 형식

### ✅ **정상 상태 응답**

```json
{
  "status": "UP",
  "timestamp": "2025-01-21T15:30:45.123Z",
  "version": "1.0.0"
}
```

### ❌ **비정상 상태 응답**

```json
{
  "status": "DOWN",
  "timestamp": "2025-01-21T15:30:45.123Z", 
  "version": "1.0.0",
  "details": {
    "error": "Database connection failed"
  }
}
```

---

## 📝 API 명세
https://eight-store-0c3.notion.site/API-254d84326363800293d6fe5bb1d4d358?source=copy_link
<img width="1203" height="740" alt="Image" src="https://github.com/user-attachments/assets/2cfc8b19-ad14-4704-8056-adf39ce5b740" />
<img width="1209" height="244" alt="Image" src="https://github.com/user-attachments/assets/a0d8e596-d0cb-48a1-941b-1a72fa33086e" />

## 🚀 개발/운영 메모

- **로컬**: `.env` 파일 관리 (`.gitignore`, `.dockerignore` 포함)  
- **컨테이너**: 빌드시 `.env` 제외, 실행 시 주입  
- **운영(Azure)**: App Service 환경변수 + Key Vault  
- **배포 전략**: App Service → ACA → AKS 단계적 고도화  

