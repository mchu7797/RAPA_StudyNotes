---
uid: 202604301604
aliases: [Authentication Header, AH]
tags: [ipsec, ah, integrity, authentication]
source: RAPA 참고자료 - VPN.pdf
created: 2026-04-30
status: complete
---
# 개념
AH(Authentication Header)는 IPsec에서 무결성과 인증을 제공하는 프로토콜이다.

## AH 특징
- IP 패킷의 일부 헤더와 페이로드에 대해 무결성 검증 수행
- 데이터 암호화는 제공하지 않으므로 기밀성 요구가 있는 환경엔 단독 사용이 부적합
- NAT가 헤더를 변경하면 검증 실패 가능성이 커 실무 활용이 제한적

# 핵심 포인트
- 데이터 **암호화(기밀성)** 는 제공하지 않는다.
- 패킷 위변조 검증 목적에 초점이 있다.
- 참고자료 기준 Cisco ASA 환경에서는 주 사용 프로토콜이 아니다.

## 언제 고려할까
- 데이터 암호화는 별도 계층에서 이미 수행하고, 무결성/인증만 추가로 필요한 경우
- 다만 운영 호환성과 장비 지원성을 고려하면 대부분 ESP 선택이 일반적

# 상위 개념
- [[IPsec]]

# 관련 개념
- [[IPsec ESP]]
- [[IKE]]

