# MSA Project Hub

**Stack**: Spring Boot (Auth/Sending) · FastAPI (Analytics) · React (Web)  
**Infra**: Azure Container Apps · Azure DB for PostgreSQL · Key Vault · ACR · (APIM optional)

> 📘 Notion: https://eight-store-0c3.notion.site/252d8432636380f6bb7ecab2ec6c48e0
> 
> 🔗 Organization: https://github.com/KTCrack01
> 

## Domains & Missions

| Service          | Domain(무엇을 다룸) | Mission(한 줄 사명) | Repo |
|---|---|---|---|
| **auth-api**     | 인증/회원            | 카카오 OAuth로 로그인 처리하고 RS256 JWT 발급/검증을 제공한다. | https://github.com/KTCrack01/api-login-svc |
| **sending-api**  | 메시징(발송)         | 템플릿·발신번호·예약 기반으로 대량 문자 발송 처리한다. | https://github.com/KTCrack01/api-sending-svc |
| **analytics-api**| 통계/청구            | 메시지 로그를 집계해 기간별 지표와 비용을 빠르게 제공한다. | https://github.com/KTCrack01/api-analytics-svc |
| **web-frontend** | 사용자 UI            | 로그인/발송/대시보드 화면을 제공 | https://github.com/KTCrack01/web-frontend |


## Architecture


## Environments


## Security Notes
- No secrets in this repo. Use **Azure Key Vault**.  
- Images/diagrams are public-safe (no private IPs/keys).
