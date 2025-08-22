# ADR-009: Secret and Config Management

## Status
Accepted

## Context
MSA 환경에서는 서비스별 DB 접속정보, API Key(OpenAI, Twilio 등), JWT Secret 등 민감정보 관리가 필요하다.  
개발/운영 환경에 따라 관리 방식이 달라야 하며, Git에 노출되지 않도록 보호가 필수적이다.

## Decision
- **로컬 개발**
  - `.env` 파일 사용
  - `.gitignore`, `.dockerignore`에 포함하여 원격 저장소/이미지에 포함되지 않도록 한다
- **컨테이너/Docker**
  - 빌드시 `.env` 제외
  - 실행 시 `-e` 옵션 또는 Compose의 `env_file`로 주입
- **Azure**
  - App Service 환경 변수(Configuration) 사용
  - 보안이 필요한 값(API Key, DB Password 등)은 **Azure Key Vault**에 저장 후 참조

## Consequences
- 👍 시크릿 노출 방지, 환경별 설정 분리 가능
- 👍 운영 시 Key Vault로 중앙 관리 → 보안성 강화
- 👎 초기 Key Vault 학습/구성이 필요
