---
uid: 202604301608
aliases: [IPsec 전송 모드, Transport Mode]
tags: [ipsec, mode, transport]
source: RAPA 참고자료 - VPN.pdf
created: 2026-04-30
status: complete
---
# 개념
IPsec Transport Mode는 원본 IP 헤더를 유지한 채 페이로드 중심으로 보호하는 방식이다.

## 언제 쓰는가
- 호스트 간(End-to-End) 직접 보안 통신
- 터널 오버헤드를 최소화하고 싶은 환경

## 장단점
- 장점: 추가 외부 헤더가 없어 오버헤드가 작음
- 단점: 원본 IP가 노출되어 주소 은닉 효과가 낮음
- 단점: 게이트웨이-게이트웨이 Site-to-Site 구조에는 부적합한 경우가 많음

# 핵심 포인트
- 종단 장비 간 직접 통신 보호에 적합하다.
- 추가 외부 IP 헤더가 없어 오버헤드는 비교적 작다.
- 원본 IP 주소가 외부 경로에 노출될 수 있다.

# 상위 개념
- [[IPsec]]

# 관련 개념
- [[IPsec Tunnel Mode]]
- [[IPsec ESP]]

