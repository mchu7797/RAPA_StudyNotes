---
uid: 202604301606
aliases: [Internet Key Exchange]
tags: [ipsec, ike, key-exchange, security]
source: RAPA 참고자료 - VPN.pdf
created: 2026-04-30
status: complete
---
# 개념
IKE는 IPsec 피어 간 인증과 키 교환, 보안 파라미터 협상을 수행하는 프로토콜이다.

## 역할 분리
- **인증(Authentication)**: 피어의 신뢰성 검증(PSK/인증서)
- **키 관리(Key Management)**: 세션 키 생성/갱신
- **협상(Negotiation)**: 암호 스위트, DH 그룹, lifetime 결정

## IKEv1 vs IKEv2
| 항목 | IKEv1 | IKEv2 |
|------|-------|-------|
| 협상 구조 | Main/Aggressive + Quick Mode | 단순화된 교환 구조 |
| 안정성/복구 | 상대적으로 약함 | 재접속/모빌리티 대응 개선 |
| 운영 난이도 | 정책 조합 복잡 | 상대적으로 단순 |

## 협상 실패의 대표 원인
- 암호/해시/DH 그룹 불일치
- PSK 불일치 또는 인증서 검증 실패
- Peer IP/NAT 환경 변화로 ID mismatch
- 양단 clock 오차로 인증서 유효기간 검증 실패

# 핵심 포인트
- 통신 시작 시 상대 장비 신뢰성 검증을 담당한다.
- PSK 또는 인증서 기반 인증 방식이 사용된다.
- SA 협상 흐름에서 핵심 제어 역할을 한다.

# 상위 개념
- [[IPsec]]

# 관련 개념
- [[ISAKMP]]
- [[IPsec ESP]]
- [[IPsec AH]]

