---
uid: 202604301605
aliases: [Encapsulating Security Payload, ESP]
tags: [ipsec, esp, encryption, integrity]
source: RAPA 참고자료 - VPN.pdf
created: 2026-04-30
status: complete
---
# 개념
ESP(Encapsulating Security Payload)는 IPsec에서 암호화 중심의 보안을 제공하는 프로토콜이다.

## 제공 기능
- Payload 암호화(기밀성)
- 무결성 검증(변조 탐지)
- 송신자 인증(공유 키 기반)
- 재전송 공격 방지(시퀀스 번호 기반)

## 동작 포인트
- Transport Mode: 상위 계층 데이터 중심 보호
- Tunnel Mode: 원본 IP 패킷 전체 보호(실무 다수)
- NAT 환경에서는 보통 NAT-T(UDP 4500)와 함께 사용

# 핵심 포인트
- 기밀성(암호화) + 무결성 + 인증을 함께 제공 가능하다.
- 실무 VPN 구성에서 AH보다 ESP가 주로 사용된다.

## 트러블슈팅 메모
- 암호화는 되는데 통신 불가: 트래픽 셀렉터(암호화 ACL) 불일치 가능성 우선 확인
- 터널은 올라오는데 끊김 반복: lifetime, DPD, MTU/MSS 조정 필요 여부 점검
- NAT 경유 시 단방향: UDP 4500 차단 여부 확인

# 상위 개념
- [[IPsec]]

# 관련 개념
- [[IPsec AH]]
- [[IPsec Tunnel Mode]]
- [[IPsec Transport Mode]]

