# ADR-008: Phonebook Service Separation

## Status
Accepted

## Context
메시징 서비스에서 단체문자 발송 시 사용자 전화번호부 기능이 필요했다.  
처음에는 메시지 서비스 내부에 붙이려 했으나, 경계가 모호해지고 결합도가 높아지는 문제가 있었다.

## Decision
전화번호부 기능을 별도 서비스(`phonebook`)로 분리하고, 전용 DB를 사용한다.  
메시징 서비스에서는 필요 시 Phonebook API를 호출하는 방식으로 통합한다.

## Consequences
- 👍 서비스 경계가 명확해짐, 재사용 가능성 증가
- 👍 독립 배포/확장이 가능함
- 👎 서비스 간 호출/통신 오버헤드가 발생
