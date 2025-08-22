# ADR-020: SMS Provider Selection (Twilio)

## Status
Accepted

## Context
메시징 서비스에서 공인알림문자/문자 발송을 위해 외부 SMS 게이트웨이가 필요하다. 현재 코드베이스는 Twilio SDK(`com.twilio.sdk:twilio`)를 사용한다.

## Decision
- 초기 공급자로 Twilio를 사용한다.
- 발신번호/규제 요건 등 국내 요구사항은 운영 이전에 별도 검토한다.
- 공급자 추상화를 유지하여 향후 교체 가능성 확보(예: KT/NHN/Kakao 비즈메시지 등).

## Consequences
- 👍 안정적 API와 풍부한 문서로 초기 구현 속도가 빠르다.
- 👍 글로벌 커버리지와 다양한 기능을 활용 가능하다.
- 👎 국내 인증/발신번호 규제와 비용 고려가 필요하다.


