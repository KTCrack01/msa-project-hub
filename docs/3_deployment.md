# 🚀 실행/배포 
> 공인알림문자 서비스의 로컬 실행부터 Azure App Service 배포까지 전체 가이드

---

## 🐳 로컬 실행

### Docker 단일 실행 (서비스별 - .env 파일 사용)

#### Backend 서비스들 (포트: 8080)
```bash
# .env 파일 준비 (각 서비스 루트 디렉토리)
# .env 예시:
# DATABASE_URL=jdbc:postgresql://localhost:5432/your-db
# DATABASE_USERNAME=postgres  
# DATABASE_PASSWORD=password
# TWILIO_ACCOUNT_SID=your-sid
# TWILIO_AUTH_TOKEN=your-token
# OPENAI_API_KEY=sk-your-key

# Docker 실행 (.env 파일 자동 로드)
docker run -p 8080:8080 --env-file .env npr04191/api-messaging-svc:latest
docker run -p 8080:8080 --env-file .env npr04191/api-analytics-svc:latest  
docker run -p 8080:8080 --env-file .env npr04191/api-phonebook-svc:latest
docker run -p 8080:8080 --env-file .env npr04191/api-login-svc:latest
docker run -p 8080:8080 --env-file .env npr04191/api-aiagent-svc:latest
```

#### Frontend (포트: 3000)
```bash
docker run -p 3000:3000 npr04191/web-frontend:latest
```

### 컨테이너 이미지 태그 규칙
- **형식**: `MMDD_HHMM` (한국 시간 기준)
- **예시**: `0821_1812` (8월 21일 오후 6시 12분)  
- **자동 생성**: GitHub Actions에서 배포 시점 기준으로 자동 태깅
- **Full 이미지명**: `docker.io/npr04191/service-name:0821_1812`

---

## 🔄 CI/CD 현황

### GitHub Actions 배지 및 워크플로우

| 서비스 | Repository | 배포 상태 |
|---|---|---|
| Frontend | [`web-frontend`](https://github.com/KTCrack01/web-frontend) | ![Deploy Status](https://github.com/KTCrack01/web-frontend/workflows/build%20&%20deploy%20(frontend)/badge.svg) |
| Messaging | [`api-messaging-svc`](https://github.com/KTCrack01/api-messaging-svc) | ![Deploy Status](https://github.com/KTCrack01/api-messaging-svc/actions/workflows/deploy.yml/badge.svg) |
| Analytics | [`api-analytics-svc`](https://github.com/KTCrack01/api-analytics-svc) | ![Deploy Status](https://github.com/KTCrack01/api-analytics-svc/actions/workflows/deploy.yml/badge.svg) |
| Phonebook | [`api-phonebook-svc`](https://github.com/KTCrack01/api-phonebook-svc) | ![Deploy Status](https://github.com/KTCrack01/api-phonebook-svc/actions/workflows/deploy.yml/badge.svg) |
| Login | [`api-login-svc`](https://github.com/KTCrack01/api-login-svc) | ![Deploy Status](https://github.com/KTCrack01/api-login-svc/actions/workflows/deploy.yml/badge.svg) |
| AI Agent | [`api-aiagent-svc`](https://github.com/KTCrack01/api-aiagent-svc) | ![Deploy Status](https://github.com/KTCrack01/api-aiagent-svc/actions/workflows/deploy.yml/badge.svg) |

### 주요 배포 단계
1. **빌드/테스트 단계**: Gradle/NPM 빌드, 테스트 실행 (병렬 처리 안함)
2. **이미지 태깅**: `MMDD_HHMM` 형식으로 한국시간 기준 자동 태깅  
3. **배포 단계**: Docker Hub 푸시 → Azure OIDC 인증 → App Service 배포

### 병렬성 및 특징
- **서비스별 독립 배포**: 각 레포별로 병렬 실행 가능
- **트리거**: `main` 브랜치 푸시 + 수동 실행(`workflow_dispatch`)
- **캐싱**: Docker 레이어 캐시 + GitHub Actions 캐시 활용

---

## 🔐 환경변수/Secret 목록

### GitHub Repository Secrets (CI/CD용)

GitHub Actions 배포를 위한 인증 정보 (강사님께 권한받아 Azure 앱등록 후 설정):

| Secret 이름 | 주입 위치 | 용도 |
|---|---|---|
| `DH_USER` | GitHub Repo Secrets | Docker Hub 인증 |
| `DH_PASS` | GitHub Repo Secrets | Docker Hub 인증 |
| `AZURE_CLIENT_ID` | GitHub Repo Secrets | Azure OIDC 인증 |
| `AZURE_TENANT_ID` | GitHub Repo Secrets | Azure OIDC 인증 |
| `AZURE_SUBSCRIPTION_ID` | GitHub Repo Secrets | Azure OIDC 인증 |
| `WEBAPP_NAME` | GitHub Repo Secrets | Azure App Service 이름 |
| `RESOURCE_GROUP` | GitHub Repo Secrets | Azure 리소스 그룹 |

### 애플리케이션 환경변수 (런타임용)

Azure App Service Configuration에 직접 설정:

#### 공통 (모든 Backend 서비스)
| 변수명 | 주입 위치 | 용도 |
|---|---|---|
| `DATABASE_URL` | Azure App Service | PostgreSQL 연결 |
| `DATABASE_USERNAME` | Azure App Service | DB 사용자명 |
| `DATABASE_PASSWORD` | Azure App Service | DB 비밀번호 |

#### api-aiagent-svc 전용
| 변수명 | 주입 위치 | 용도 |
|---|---|---|
| `OPENAI_API_KEY` | Azure App Service | OpenAI API 인증 |
| `OPENAI_API_URL` | Azure App Service | OpenAI API 엔드포인트 |

#### api-messaging-svc 전용
| 변수명 | 주입 위치 | 용도 |
|---|---|---|
| `TWILIO_ACCOUNT_SID` | Azure App Service | Twilio 계정 ID |
| `TWILIO_AUTH_TOKEN` | Azure App Service | Twilio 인증 토큰 |
| `MESSAGE_URL` | Azure App Service | 메시지 서비스 URL |
| `MESSAGE_DASHBOARD_URL` | Azure App Service | 대시보드 API URL |


---

## 🏥 헬스체크 경로

### 기본 헬스체크: `/actuator/health`

| 서비스 | 헬스체크 URL | 테스트 결과 |
|---|---|---|
| **api-analytics-svc** | `https://analytics-svc-aucrheemh4edbtac.koreacentral-01.azurewebsites.net/actuator/health` | ✅ `{"status":"UP"}` |
| **api-messaging-svc** | `https://messaging-svc-a0euekhwgueqd7c0.koreacentral-01.azurewebsites.net/actuator/health` | ✅ `{"status":"UP"}` |
| **api-phonebook-svc** | `https://phonebook-svc-dtd4f8f9cyfee5c0.koreacentral-01.azurewebsites.net/actuator/health` | ✅ `{"status":"UP"}` |
| **api-login-svc** | `https://login-svc-gbg8ephsd6bufnca.koreacentral-01.azurewebsites.net/actuator/health` | ✅ `{"status":"UP"}` |
| **api-aiagent-svc** | `https://aiagent-svc-dka3epddc7f5hdbm.koreacentral-01.azurewebsites.net/actuator/health` | ✅ `{"status":"UP"}` |
| **web-frontend** | `https://web-frontend-ffasfgacfyceeagj.koreacentral-01.azurewebsites.net/` | ✅ 정상 작동 |

### 커스텀 헬스 엔드포인트

현재는 **모든 서비스에서 기본 헬스체크만 사용** 중입니다.
- 추후 필요시 서비스별 특화된 커스텀 헬스체크 추가 예정
- 예: OpenAI API 연결 상태, Twilio API 상태 등

### Azure App Service 헬스체크 설정
- **Backend 서비스들**: `/actuator/health` 사용
- **Frontend**: `/` 기본 경로 사용

---


