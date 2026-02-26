---
uid: 202601210909
aliases: [Inter-VLAN Routing, VLAN 간 라우팅, Router-on-a-Stick, SVI 라우팅]
tags: [vlan, routing, layer3, inter-vlan, svi]
source: 260121_네트워크_이론_5.pdf
created: 2026-01-21
status: complete
---
# 개념
서로 다른 VLAN에 속한 호스트 간의 통신을 가능하게 하는 기술. L2 스위치만으로는 VLAN 간 통신이 불가능하므로 라우터 또는 L3 스위치가 필요하다.

# 핵심 포인트
- **문제**: VLAN은 독립된 브로드캐스트 도메인 → 다른 VLAN 간 통신은 L3 장비 필요
- **방법 1: 라우터 활용 (Router-on-a-Stick)**
  - 스위치의 Trunk 포트를 라우터에 연결
  - 라우터에 서브인터페이스(Sub-interface) 생성 후 각 VLAN에 IP 할당
  - 단점: 라우터의 단일 물리 포트를 모든 VLAN이 공유 → 병목현상 발생 가능
- **방법 2: L3 스위치 SVI 활용** (권장)
  - 각 VLAN에 SVI(가상 인터페이스) 생성 후 IP 주소 할당
  - `ip routing` 으로 L3 라우팅 활성화
  ```
  SW1(config)# ip routing
  SW1(config)#interface vlan 10
  SW1(config-if)#ip address 192.168.10.254 255.255.255.0
  SW1(config-if)#no shutdown
  SW1(config)#interface vlan 20
  SW1(config-if)#ip address 192.168.20.254 255.255.255.0
  SW1(config-if)#no shutdown
  ```
  - 장점: 스위치 내부에서 처리 → 빠름, 별도 라우터 불필요
- 각 VLAN 호스트의 Default Gateway = 해당 VLAN SVI IP

# 나만의 언어로
<!-- 이 개념을 누군가에게 설명한다면? 비유, 요약, 한 줄 정리 등 -->
VLAN은 독립된 방. 방 간 이동(통신)을 하려면 복도(라우터/L3 스위치)가 필요하다. SVI 방식은 빌딩 자체(L3 스위치)에 내부 복도를 만드는 것.

# 상위 개념
- [[VLAN]]

# 관련 개념
- [[Multi-Layer Switch]]
- [[Default Gateway]]
- [[802.1Q Trunk]]
- [[IP 라우팅]]
