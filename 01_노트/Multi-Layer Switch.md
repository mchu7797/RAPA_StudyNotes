---
uid: 202601210908
aliases: [Multi-Layer Switch, L3 Switch, MLS, 멀티레이어 스위치, SVI, Routed Port]
tags: [switch, layer3, routing, svi, multilayer]
source: 260121_네트워크_이론_5.pdf
created: 2026-01-21
status: complete
---
# 개념
L2 스위칭뿐만 아니라 L3 라우팅도 수행하는 스위치. VLAN 간 라우팅(Inter-VLAN Routing)을 라우터 없이 스위치 자체에서 처리할 수 있다.

# 핵심 포인트
- **L2 스위치**: MAC 주소 기반 프레임 전달, VLAN 내부 통신만 가능
- **Multi-Layer Switch (L3 Switch)**: L2 동작 + **L3 라우팅** + L4 기준 필터링 가능, VLAN 간 통신 가능
- **SVI (Switch Virtual Interface)** 방식
  - 각 VLAN에 가상 인터페이스를 만들고 IP 주소 할당 → VLAN의 Default Gateway로 사용
  - `ip routing` 명령으로 L3 라우팅 활성화 필수
  ```
  SW1(config)# ip routing
  SW1(config)#interface vlan 10
  SW1(config-if)#no shutdown
  SW1(config-if)#ip address 192.168.10.254 255.255.255.0
  SW1(config)#interface vlan 20
  SW1(config-if)#no shutdown
  SW1(config-if)#ip address 192.168.20.254 255.255.255.0
  ```
  - **SVI 활성 조건**: 해당 VLAN이 존재하고, 해당 VLAN에 속한 포트가 최소 하나 이상 Active 상태여야 함
- **Routed Port** 방식
  - 스위치 포트를 `no switchport` 설정으로 L3 포트(라우터 인터페이스)로 변환
  - IP 주소를 직접 할당하여 라우터 인터페이스처럼 동작
  ```
  SW3(config)#interface fa0/16
  SW3(config-if)#no switchport
  SW3(config-if)#ip address 192.168.10.254 255.255.255.0
  ```
- SVI 또는 Routed Port를 이용해 **동적 라우팅 프로토콜(EIGRP, OSPF)** 동작 가능

# 나만의 언어로
<!-- 이 개념을 누군가에게 설명한다면? 비유, 요약, 한 줄 정리 등 -->
L2 스위치가 "배달부"라면, L3 스위치는 "배달부 + 내비게이션 탑재". VLAN 간 통신을 위해 별도 라우터 없이 스위치 자체에서 처리할 수 있다.

# 상위 개념
- [[LAN Switching]]

# 관련 개념
- [[Inter-VLAN Routing]]
- [[VLAN]]
- [[IP 라우팅]]
- [[EtherChannel]]
