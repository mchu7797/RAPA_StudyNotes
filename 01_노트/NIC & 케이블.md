---
uid: 202601120901
aliases: [Network Interface Card, LAN카드, UTP, 광케이블]
tags: [hardware, physical, layer1]
source: 260112_네트워크_이론.pdf
created: 2026-01-12
status: complete
---
# 개념
NIC(Network Interface Card)는 컴퓨터를 네트워크에 연결하는 H/W로, 케이블을 통해 데이터를 신호로 변환한다.

# 핵심 포인트
- **NIC**: 컴퓨터 데이터를 UTP/Fiber 케이블로 전달 가능한 신호로 변환, 고유 MAC 주소 보유
  - 네트워크 어댑터 / 인터페이스 카드 / LAN카드 / 이더넷 카드 등 다양한 명칭
- **UTP(xTP) 케이블**: 8가닥 구리선(2가닥씩 꼬임), RJ-45 커넥터 사용
  - Cat5 (100Mbps) → Cat5e (1Gbps) → Cat6 (1Gbps) → Cat6a (10Gbps) → Cat7 (10Gbps) → Cat8 (40Gbps)
  - 실드 종류: U(비차폐), F(포일 차폐), S(브레이드 차폐)
- **광섬유(Fiber) 케이블**: 빛을 이용, 노이즈 영향 적고 장거리 전송 가능 (대륙 간 연결)
  - Single Mode: 8~10㎛ 코어, 40~100km 전송
  - Multi Mode: 50~62.5㎛ 코어, 550m 전송
  - 커넥터: LC, SC, FC 등

# 나만의 언어로
<!-- 이 개념을 누군가에게 설명한다면? 비유, 요약, 한 줄 정리 등 -->
NIC는 컴퓨터의 "귀와 입" 역할. UTP는 가까운 거리 일반 LAN용, 광케이블은 멀고 빠른 연결용으로 쓴다. Cat 숫자가 클수록 더 빠르다.

# 상위 개념
- [[컴퓨터 구조]]
- OSI Layer 1 (Physical)

# 관련 개념
- [[MAC 주소]]
- [[네트워크 기초]]
- [[네트워크 속도 (Bandwidth)]]
