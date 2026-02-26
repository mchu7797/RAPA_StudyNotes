---
uid: 202601210907
aliases: [EtherChannel, Port-channel, PAgP, LACP, Link Aggregation, 링크 묶기]
tags: [etherchannel, switch, layer2, layer3, redundancy, bandwidth]
source: 260121_네트워크_이론_5.pdf
created: 2026-01-21
status: complete
---
# 개념
여러 개의 물리적 링크를 하나의 논리적 링크로 묶어 대역폭을 늘리고 이중화를 동시에 구현하는 기술. STP는 EtherChannel을 단일 논리 링크로 인식하여 Block하지 않는다.

# 핵심 포인트
- **EtherChannel의 필요성**: 스위치 간 링크가 부족 → 링크 추가 시 STP가 하나를 Block → 해결: EtherChannel로 묶으면 STP가 단일 링크로 인식 → 모든 물리 링크 동작
- **EtherChannel 조건**: 묶는 인터페이스들의 Duplex, Speed, Native/Allowed VLAN, Switchport mode가 동일해야 함
- **협상 프로토콜 3가지**
  | 방식 | 프로토콜 | 모드 조합 |
  |------|----------|----------|
  | **PAgP** (Cisco 전용) | `desirable` / `auto` | desirable-desirable ✅ / desirable-auto ✅ / auto-auto ❌ |
  | **LACP** (IEEE 표준) | `active` / `passive` | active-active ✅ / active-passive ✅ / passive-passive ❌ |
  | **Manual** | `on` / `on` | on-on ✅ (협상 없이 강제 묶음) |
- **L2 EtherChannel 설정 (PAgP 예시)**:
  ```
  SW1(config)#interface range GigabitEthernet 0/1 - 2
  SW1(config-if)#channel-group 1 mode desirable

  SW1(config)#interface Port-channel 1
  SW1(config-if)#switchport trunk encapsulation dot1q
  SW1(config-if)#switchport mode trunk
  ```
- **L3 EtherChannel**: 물리 인터페이스에 `no switchport` 설정 후 Port-channel에 IP 할당
  ```
  SW1(config-if-range)#no switchport
  SW1(config-if-range)#channel-group 12 mode on
  SW1(config)#interface port-channel 12
  SW1(config-if)#ip address 192.168.12.1 255.255.255.0
  ```
- **설정 변경 주의**: 인터페이스 설정 변경은 반드시 Port-Channel 인터페이스에서 수행 → 물리 인터페이스에 자동 반영
- `show etherchannel summary`: EtherChannel 상태 확인 (SU = S(L2)+U(사용중), P = bundled)

# 나만의 언어로
<!-- 이 개념을 누군가에게 설명한다면? 비유, 요약, 한 줄 정리 등 -->
여러 차선(물리 링크)을 하나의 고속도로(논리 링크)로 합치는 것. 대역폭이 늘고, 하나가 끊겨도 나머지로 계속 달린다. STP 입장에서는 고속도로 전체가 "링크 1개"로 보인다.

# 상위 개념
- [[LAN Switching]]

# 관련 개념
- [[STP]]
- [[802.1Q Trunk]]
- [[Multi-Layer Switch]]
