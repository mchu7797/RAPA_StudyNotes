---
uid: 202604301612
aliases: [AnyConnect SSL VPN, Full Tunnel SSL VPN]
tags: [ssl-vpn, anyconnect, tunnel-mode, remote-access]
source: RAPA 참고자료 - SSL VPN.pdf
created: 2026-04-30
status: complete
---
# 개념
SSL VPN Tunnel Mode는 AnyConnect 같은 클라이언트를 사용해 단말-사내망 간 터널을 구성하는 방식이다.

## 동작 포인트
- 접속 후 가상 인터페이스를 생성하고 사내 정책(DNS, 라우트, ACL)을 단말에 반영
- Clientless/Thin-Client보다 넓은 범위의 트래픽을 보호
- 필요 시 Always-On VPN, Posture 검사와 결합 가능

## 운영 설계 항목
1. Full Tunnel vs Split Tunnel
2. 사용자 그룹별 접근 대역 분리
3. 클라이언트 업데이트/배포 방식(자동 배포, 버전 고정)
4. 단말 보안 기준(Posture: AV, OS Patch, Disk Encryption)

## 장애 시 점검 순서
- 인증 단계 실패(계정/MFA/인증서)
- 터널은 연결되나 내부 접근 불가(라우팅/ACL/DNS)
- 특정 SaaS 품질 저하(Split Tunnel 예외 정책)

# 핵심 포인트
- Clientless보다 넓은 범위의 애플리케이션 트래픽 보호가 가능하다.
- 사실상 전용 VPN 클라이언트 기반 원격 접속 모델이다.
- 정책/권한 설계를 잘못하면 과도한 네트워크 접근을 허용할 수 있다.

# 상위 개념
- [[SSL VPN]]

# 관련 개념
- [[SSL VPN Clientless]]
- [[SSL VPN Thin-Client]]
- [[Client-to-Site VPN]]
- [[IPsec]]

