---
uid: 202604301558
aliases: [Virtual Private Network, IPsec VPN, Site-to-Site VPN, Client-to-Site VPN]
tags: [vpn, security, ipsec, tunneling]
source: RAPA 참고자료 - VPN.pdf
created: 2026-04-30
status: complete
---
# 개념
VPN(Virtual Private Network)은 공용망(인터넷) 위에 가상의 사설 통신 경로(터널)를 만들어, 전용선처럼 안전하게 통신하도록 하는 기술이다.

## 하위 개념
- [[Tunneling]]
- [[Site-to-Site VPN]]
- [[Client-to-Site VPN]]
- [[IPsec]]
- [[IPsec AH]]
- [[IPsec ESP]]
- [[IKE]]
- [[ISAKMP]]
- [[IPsec Transport Mode]]
- [[IPsec Tunnel Mode]]

## 왜 VPN을 쓰는가
- **비용 절감**: 전용선 대비 저비용으로 지점 간 보안 연결 구성
- **유연성**: 본사-지사, 클라우드, 재택 사용자까지 동일 원리로 확장
- **보안 강화**: 공용망 구간에서 암호화/무결성/인증 적용

## VPN 기본 구성요소
- **VPN Gateway**: 터널 종단(라우터, 방화벽, VPN Concentrator)
- **Tunneling Protocol / Security Protocol**: 터널 형성 및 보호(IPsec, SSL/TLS)
- **인증 체계**: PSK, 인증서, 사용자 계정(AAA/RADIUS/LDAP)
- **정책 제어**: 접근 제어, 암호화 스위트, 라우팅/분할 터널 정책

## 설계 시 핵심 체크포인트
1. 연결 목적: Site-to-Site vs Client-to-Site
2. 보호 범위: 전체 트래픽(Full Tunnel) vs 업무 트래픽(Split Tunnel)
3. 경로/주소 정책: 라우팅, NAT 예외, 중복 대역 충돌 여부
4. 운영성: 인증서 갱신, 로그/모니터링, 장애 시 우회 경로

# 핵심 포인트
- VPN의 핵심 축은 **터널링**, **접속 형태**, **보안 프로토콜(IPsec)** 이다.
- 제텔카스텐 구조에서는 세부 개념을 개별 노트로 분리해 상호 링크로 탐색한다.

# 상위 개념
- [[네트워크 기초]]

# 관련 개념
- [[Firewall]]
- [[ASA]]
- [[SSL VPN]]
