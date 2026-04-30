---
uid: 202604301600
aliases: [터널링, 캡슐화 터널링]
tags: [vpn, tunneling, encapsulation, security]
source: RAPA 참고자료 - VPN.pdf
created: 2026-04-30
status: complete
---
# 개념
터널링(Tunneling)은 원본 패킷을 다른 헤더로 감싸 공용망을 통과시킨 뒤, 목적지에서 복원하는 기술이다.

## 터널링 단계
1. 원본 패킷 생성(내부 주소 포함)
2. 터널 엔드포인트에서 캡슐화(새 외부 헤더 부착)
3. 공용망 라우팅(외부 헤더 기준 전달)
4. 반대편 엔드포인트에서 디캡슐화 후 내부로 전달

## 장점과 한계
- 장점: 논리적 사설 링크 구성, 주소 은닉, 보안 프로토콜 결합 용이
- 한계: 헤더 오버헤드 증가로 MTU 감소, 조각화/성능 이슈 가능

## 운영 팁
- VPN 터널 환경에서 대용량 전송 불안정 시 MTU/MSS 튜닝부터 점검
- 경로 MTU Discovery 차단 환경에서는 fragmentation 이슈가 빈번

# 핵심 포인트
- VPN의 기본 동작은 **캡슐화(Encapsulation) → 전송 → 디캡슐화(Decapsulation)** 이다.
- 공용망 위에서도 논리적으로는 사설 링크처럼 통신할 수 있다.

# 상위 개념
- [[VPN]]

# 관련 개념
- [[IPsec]]
- [[Site-to-Site VPN]]
- [[Client-to-Site VPN]]

