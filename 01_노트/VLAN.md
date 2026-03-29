---
uid: 202601210901
aliases: [Virtual LAN, VLAN, 브로드캐스트 도메인 분리, 논리적 네트워크 분리]
tags: [vlan, switch, layer2, broadcast]
source: 260121_네트워크_이론_5.pdf
created: 2026-01-21
status: complete
---
# 개념
물리적 연결과 관계없이 스위치 포트를 논리적으로 그룹화하는 기술. 각 VLAN은 독립된 브로드캐스트 도메인으로 동작한다.

# 핵심 포인트
- VLAN = 단일 브로드캐스트 도메인 → **같은 VLAN끼리만 Broadcast 수신**
- 다른 VLAN 간 통신: **L3 스위치 또는 라우터** 필요
- **VLAN의 필요성**
  1. Broadcast 범위 제한 → 성능 향상
  2. 장비/스위치 장애 시 영향 범위 격리
  3. 부서 간 보안 강화
- 기본 VLAN: **VLAN 1** (모든 포트 기본 소속, 삭제 불가)
- **VLAN 설정**:
  ```
  SW1(config)#vlan 50
  SW1(config-vlan)#name Computers
  SW1(config)#interface fa0/1
  SW1(config-if)#switchport mode access
  SW1(config-if)#switchport access vlan 50
  ```
- `show vlan`: Access 모드 포트만 표시 (Trunk 포트는 미표시)
- `show interfaces fa0/x switchport`: 포트 VLAN 설정 상세 확인

같은 건물에 여러 회사가 있을 때, 물리적으로는 같은 스위치에 연결되어 있어도 논리적으로는 완전히 다른 네트워크처럼 분리할 수 있다.

# 상위 개념
- [[LAN Switching]]

# 관련 개념
- [[802.1Q Trunk]]
- [[IP 라우팅]]
- [[Network Design (Campus)]]
