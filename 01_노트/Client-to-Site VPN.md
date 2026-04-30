---
uid: 202604301602
aliases: [Remote User VPN, Remote Access VPN]
tags: [vpn, remote-access, security]
source: RAPA 참고자료 - VPN.pdf, SSL VPN.pdf
created: 2026-04-30
status: complete
---
# 개념
Client-to-Site VPN은 외부의 개별 사용자가 사내망으로 안전하게 접속하는 방식이다.

## 접속 절차(공통)
1. 사용자가 VPN 게이트웨이 URL/IP로 접속
2. 사용자/단말 인증(계정, 인증서, MFA)
3. 접속 정책 할당(허용 대역, DNS, Split/Full Tunnel)
4. 세션 생성 후 내부 리소스 접근

## 설계 포인트
- **인증 강화**: MFA, 단말 인증서, 그룹 기반 권한 분리
- **접근 최소화**: 업무 시스템 기준으로 세분화된 ACL 적용
- **터널 정책**: Full Tunnel은 보안 강하지만 대역폭 부담, Split Tunnel은 성능 유리하지만 보안 통제 보완 필요
- **엔드포인트 보안**: 패치/백신 상태(Posture) 점검이 중요

## 운영 지표
- 동시 접속자 수(license/capacity)
- 인증 실패율(MFA/계정 잠금 포함)
- 세션 평균 유지 시간 및 재연결률

# 핵심 포인트
- 사용자 단말이 VPN 클라이언트 또는 브라우저로 터널을 형성한다.
- 재택/외부 근무 환경의 표준 원격 접속 구조다.
- 구현 기술은 크게 IPsec Remote Access와 SSL VPN으로 나뉜다.

# 상위 개념
- [[VPN]]

# 관련 개념
- [[Site-to-Site VPN]]
- [[SSL VPN]]
- [[IPsec]]

