---
uid: 202604301607
aliases: [Internet Security Association and Key Management Protocol]
tags: [ipsec, isakmp, sa, key-management]
source: RAPA 참고자료 - VPN.pdf
created: 2026-04-30
status: complete
---
# 개념
ISAKMP는 IPsec에서 보안 연관(SA) 생성/관리 절차를 정의하는 키 관리 프레임워크다.

## ISAKMP가 다루는 것
- SA 생성/삭제/재협상 절차
- 메시지 형식과 교환 순서
- 협상 대상 파라미터(암호 알고리즘, 해시, DH, lifetime) 운반

## 실무 관점 정리
- ISAKMP는 "협상 프레임"이고, IKE는 이를 활용해 실제 키 교환/인증 수행
- 장비 설정에서는 `isakmp policy`(v1) 또는 `ikev2 policy/proposal` 형태로 노출
- 정책 순서(priority)와 매칭 조건이 잘못되면 협상 자체가 시작되지 않음

# 핵심 포인트
- 어떤 알고리즘/정책으로 통신할지 협상 구조를 제공한다.
- IKE와 함께 동작해 실제 키 교환 및 인증 흐름을 완성한다.

# 상위 개념
- [[IPsec]]

# 관련 개념
- [[IKE]]
- [[IPsec ESP]]

