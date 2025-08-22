# ADR-004: Database Per Service

## Status
Accepted

## Context
MSA에서 모든 서비스가 하나의 DB를 공유할지, 서비스별로 분리할지 논의됨.

## Decision
각 서비스(Messaging, Analytics, Phonebook, Login)가 독립된 DB를 사용한다.

## Consequences
- 👍 결합도 낮아짐, 서비스 단위 확장/장애 격리 가능
- 👎 운영 시 DB 관리 오버헤드 증가
