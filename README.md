# MSA Project Hub

**Stack**: Spring Boot (Auth/Sending) · FastAPI (Analytics) · React (Web)  
**Infra**: Azure Container Apps · Azure DB for PostgreSQL · Key Vault · ACR · (APIM optional)

> 📘 Notion: https://eight-store-0c3.notion.site/252d8432636380f6bb7ecab2ec6c48e0
> 🔗 Organization: https://github.com/<org>

## Repository Map
| Domain | Repo | Tech | Link |
|---|---|---|---|
| Auth | auth-api | Spring Boot | https://github.com/<org>/auth-api |
| Sending | sending-api | Spring Boot | https://github.com/<org>/sending-api |
| Analytics | analytics-api | FastAPI | https://github.com/<org>/analytics-api |
| Web | web-frontend | React | https://github.com/<org>/web-frontend |
| Infra | infra-azure | IaC / Scripts | https://github.com/<org>/infra-azure |

## Architecture
- C4 L2 (Containers): `diagrams/c4-l2-containers.png`
- Login Sequence: `diagrams/seq-login.md`
- Message Flow: `diagrams/seq-message.md`
- ERD: `diagrams/erd.png`

## Environments
- Dev: `https://api.dev.example.com` (APIM) / Web: `https://app.dev.example.com`
- Prod: `https://api.example.com` / Web: `https://app.example.com`

## Security Notes
- No secrets in this repo. Use **Azure Key Vault**.  
- Images/diagrams are public-safe (no private IPs/keys).
