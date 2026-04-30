---
uid: 202604301559
aliases: [TLS VPN, WebVPN, Clientless VPN, AnyConnect]
tags: [vpn, ssl, tls, remote-access, security]
source: RAPA 참고자료 - SSL VPN.pdf
created: 2026-04-30
status: complete
---
# 개념
SSL VPN은 TLS/SSL(TCP 443) 기반으로 원격 사용자가 사내 리소스에 안전하게 접속하도록 하는 Remote Access VPN 방식이다.

IPsec VPN이 네트워크 계층 중심의 터널이라면, SSL VPN은 **애플리케이션 접근 게이트웨이** 성격이 강하다.

## 동작 개요
1. 사용자 브라우저/클라이언트가 VPN 게이트웨이에 HTTPS(443) 연결
2. 인증서 검증 + 사용자 인증(계정, MFA 등)
3. 정책에 따라 Clientless/Thin-Client/AnyConnect 세션 할당
4. 허용된 내부 리소스만 프록시 또는 터널 방식으로 접근

## IPsec Remote Access와 실무 비교
| 항목 | SSL VPN | IPsec RA VPN |
|------|---------|--------------|
| 기본 포트 | TCP 443 | UDP 500/4500 (NAT-T), ESP |
| 접속 편의성 | 높음(브라우저/클라이언트) | 보통(클라이언트 중심) |
| 앱 호환성 | 모드에 따라 제한 가능 | 네트워크 단위 보호에 강함 |
| 방화벽 통과성 | 상대적으로 유리 | 환경 따라 제약 가능 |
| 대표 사용처 | 재택/외부 사용자 원격접속 | 관리형 단말 중심 원격접속 |

## 하위 개념
- [[SSL VPN Clientless]]
- [[SSL VPN Thin-Client]]
- [[SSL VPN Tunnel Mode (AnyConnect)]]
- [[Client-to-Site VPN]]

## 운영 시 주의사항
- 사용자 인증은 계정+MFA 조합으로 강화
- 접근 권한은 업무 단위 최소 권한(서브넷/애플리케이션 기준)
- Split Tunnel 사용 시 로컬 인터넷 경유 트래픽 보안 정책 별도 설계
- 인증서 만료/CRL/OCSP 실패 시 접속 장애가 빈번하므로 사전 모니터링 필요

# 핵심 포인트
- SSL VPN은 Remote Access VPN 계열에서 **접속 편의성**을 강화한 방식이다.
- 접속 모델(Clientless/Thin-Client/Tunnel)은 접근 범위와 운영 복잡도를 결정한다.

# 상위 개념
- [[VPN]]

# 관련 개념
- [[Firewall]]
- [[ASA]]
- [[IPsec]]
