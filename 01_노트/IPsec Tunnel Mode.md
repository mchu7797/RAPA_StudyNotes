---
uid: 202604301609
aliases: [IPsec 터널 모드, Tunnel Mode]
tags: [ipsec, mode, tunnel, site-to-site]
source: RAPA 참고자료 - VPN.pdf
created: 2026-04-30
status: complete
---
# 개념
IPsec Tunnel Mode는 원본 IP 패킷 전체를 보호하고, 외부 전송용 새 IP 헤더를 추가하는 방식이다.

## 왜 Site-to-Site에 적합한가
- 내부 원본 주소를 외부에 직접 노출하지 않음
- 양 끝 VPN 게이트웨이가 암복호화를 담당해 사용자 단말 부담이 작음
- 지점 간 대역 전체를 정책 단위로 보호하기 쉬움

## 설계 시 고려사항
- 캡슐화 오버헤드로 MTU 감소 가능
- 대규모 환경에서는 QoS/암호화 성능(CPU, 가속칩) 확인 필요
- 암호화 대상 대역과 라우팅/ACL/no-NAT 순서 일관성 필수

# 핵심 포인트
- VPN 게이트웨이 간 Site-to-Site 연결에 가장 일반적으로 사용된다.
- 내부 주소 은닉과 보안 경계 분리에 유리하다.

# 상위 개념
- [[IPsec]]

# 관련 개념
- [[IPsec Transport Mode]]
- [[Site-to-Site VPN]]
- [[IPsec ESP]]

