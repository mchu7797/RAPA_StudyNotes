---
uid: 202604301601
aliases: [사이트 간 VPN, Gateway-to-Gateway VPN]
tags: [vpn, site-to-site, ipsec, security]
source: RAPA 참고자료 - VPN.pdf
created: 2026-04-30
status: complete
---
# 개념
Site-to-Site VPN은 본사-지사처럼 **네트워크와 네트워크**를 VPN 게이트웨이끼리 연결하는 방식이다.

## 전형적인 구성
- 본사 VPN Gateway 1대 + 지사 VPN Gateway 1대
- 내부 대역(예: HQ 10.10.0.0/16, Branch 10.20.0.0/16) 간 암호화 정책 적용
- 동적 라우팅(OSPF/BGP) 또는 정적 라우팅으로 경로 교환

## 설계 포인트
1. 암호화 대상 대역(interesting traffic) 정확히 정의
2. NAT 예외 규칙(no-NAT)과 암호화 정책 순서 일치
3. 이중 회선/이중 장비 시 failover 시나리오 구성
4. 중복 IP 대역 존재 시 NAT 또는 재주소 설계 필요

## 장애 패턴
- 터널은 up인데 통신 불가: 암호화 ACL/라우팅/no-NAT 불일치
- 간헐적 다운: DPD, keepalive, 회선 품질 문제
- 특정 앱만 실패: MTU/MSS 또는 PMTUD 이슈

# 핵심 포인트
- 터널 양 끝은 보통 라우터/방화벽 장비다.
- 내부 사용자는 별도 VPN 클라이언트 없이 상대 사이트 자원에 접근한다.
- 실무에서는 IPsec Tunnel Mode를 주로 사용한다.

# 상위 개념
- [[VPN]]

# 관련 개념
- [[Tunneling]]
- [[IPsec]]
- [[IPsec Tunnel Mode]]
- [[Client-to-Site VPN]]

