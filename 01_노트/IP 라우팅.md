---
uid: 202601280900
aliases: [IP Routing, 라우터, 라우팅 테이블, Routing Table, Static Routing, Default Route]
tags: [routing, layer3, router, ip]
source: 260128_네트워크_이론_6.pdf
created: 2026-01-28
status: complete
---
# 개념
라우터가 IP 패킷의 목적지 IP를 확인하여 올바른 경로로 전달하는 과정. 라우팅 테이블을 참조해 Next-hop을 결정한다.

# 핵심 포인트
- **스위치 vs 라우터**
  - 스위치: MAC 주소(L2) 기반 이더넷 프레임 전달 (Switching)
  - 라우터: IP 주소(L3) 기반 IP 패킷 전달 (Routing)
- **라우팅 테이블 경로 유형**
  - **Connected (C)**: 라우터 인터페이스에 직접 연결된 네트워크 (자동 등록)
  - **Static (S)**: 관리자가 수동 입력, AD=1 (Connected 다음으로 신뢰도 높음)
  - **Dynamic**: 라우팅 프로토콜로 자동 학습 (EIGRP, OSPF, RIP 등)
  - **Default Route (S*)**: 일치하는 경로 없을 때 마지막으로 참조 (`ip route 0.0.0.0 0.0.0.0 NH`)
- **IP 라우팅 과정** (H1 → H2, 다른 네트워크)
  1. H1: 서브넷 마스크로 목적지가 다른 네트워크 확인 → Default Gateway로 전달
  2. R1: FCS 확인 → Decapsulation → IP Checksum 확인 → 라우팅 테이블 조회 → **TTL 감소** → 새 이더넷 프레임 생성 → Next-hop으로 전달
  3. R2: 동일 과정 반복 → 목적지 네트워크가 직접 연결 → H2에게 전달
- **핵심 원칙**: L2 주소(MAC)는 홉마다 변경, **L3 주소(IP)는 출발지~목적지까지 불변**
- **Static Routing 명령**: `ip route [목적지 네트워크] [서브넷마스크] [Next-hop IP]`
- **Floating Static**: AD 값 높게 설정 → 기본 경로 장애 시 백업 경로로 활성화
- AD (Administrative Distance): 낮을수록 신뢰도 높음 (Connected=0, Static=1, OSPF=110, RIP=120)

# 나만의 언어로
<!-- 이 개념을 누군가에게 설명한다면? 비유, 요약, 한 줄 정리 등 -->
라우터는 내비게이션이 달린 우체부. 목적지(IP)를 보고 어느 방향으로 보낼지(라우팅 테이블) 결정하고, 다음 우체국(Next-hop)으로 넘긴다. 매 홉마다 봉투(MAC)는 바꾸지만 편지 내용(IP)은 그대로.

# 상위 개념
- [[TCP-IP 모델]]

# 관련 개념
- [[IPv4 주소 & 클래스]]
- [[Default Gateway]]
- [[ARP]]
- [[Dynamic Routing Protocol]]
- [[Static Routing]]
