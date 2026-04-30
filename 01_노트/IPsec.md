---
uid: 202604301603
aliases: [IP Security, IPSec VPN]
tags: [ipsec, vpn, security, network-layer]
source: RAPA 참고자료 - VPN.pdf
created: 2026-04-30
status: complete
---
# 개념
IPsec은 IP 계층에서 VPN 트래픽을 보호하기 위한 표준 프레임워크로, 암호화/무결성/인증을 제공한다.

## IPsec 처리 흐름(요약)
1. 피어 식별 및 정책 매칭(interesting traffic)
2. IKE를 통한 인증/키 교환
3. SA(Security Association) 생성(Phase 1/2 또는 IKEv2 Child SA)
4. ESP/AH로 데이터 보호 후 터널 송수신
5. 수신 측에서 무결성 검증, 복호화, 재조립

## SA(Security Association)
- 한 방향(uni-direction) 보안 연결 단위
- 포함 정보: 암호 알고리즘, 무결성 알고리즘, 키 수명(lifetime), SPI
- 실제 통신은 송신/수신 각각 SA를 사용하므로 보통 쌍(pair)으로 동작

## 주요 포트/프로토콜
- IKE: UDP 500
- NAT-T: UDP 4500
- 데이터 평면: ESP(IP Protocol 50), AH(IP Protocol 51)

# 핵심 포인트
- 제공 보안: **기밀성, 무결성, 인증, 재전송 공격 방지**
- 구성 요소: [[IPsec AH]], [[IPsec ESP]], [[IKE]], [[ISAKMP]], SA(Security Association)
- VPN 구현에서 Site-to-Site 구간의 대표 기술이다.

## 장애 시 먼저 보는 항목
1. 양단 암호화 정책 불일치(암호/해시/DH 그룹)
2. 인증 불일치(PSK 오타, 인증서 체인 문제)
3. NAT-T/방화벽 차단(UDP 500/4500, ESP)
4. 트래픽 셀렉터/암호화 ACL 불일치
5. SA lifetime 또는 DPD 설정 차이

# 상위 개념
- [[VPN]]

# 관련 개념
- [[IPsec AH]]
- [[IPsec ESP]]
- [[IKE]]
- [[ISAKMP]]
- [[IPsec Transport Mode]]
- [[IPsec Tunnel Mode]]

