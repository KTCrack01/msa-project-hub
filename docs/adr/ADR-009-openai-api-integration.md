# ADR-009: OpenAI API Integration

## Status
Accepted

## Context
AI Agent 호출을 프론트에서 할지, 백엔드에서 할지 논의됨.

## Decision
보안을 위해 **Backend에서 OpenAI API 호출**.  
- 로컬 개발: `.env` 파일로 관리하고 gitignore/dockerignore 처리  
- Docker: 빌드시 env 파일 제외  
- Azure: App Service 환경변수 또는 Key Vault로 관리  

## Consequences
- 👍 Key 노출 방지, 중앙 관리 가능
- 👎 서버 부하 증가 가능
