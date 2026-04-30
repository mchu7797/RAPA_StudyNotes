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

## 하위 개념
- [[SSL VPN Clientless]]
- [[SSL VPN Thin-Client]]
- [[SSL VPN Tunnel Mode (AnyConnect)]]
- [[Client-to-Site VPN]]

# 핵심 포인트
- SSL VPN은 Remote Access VPN 계열에서 **접속 편의성**을 강화한 방식이다.
- 접속 모델(Clientless/Thin-Client/Tunnel)은 접근 범위와 운영 복잡도를 결정한다.

# 상위 개념
- [[VPN]]

# 관련 개념
- [[Firewall]]
- [[ASA]]
- [[IPsec]]
