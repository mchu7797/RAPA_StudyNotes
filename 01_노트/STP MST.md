---
uid: 202601210905
aliases: [MST, Multiple Spanning Tree, 802.1s, STP 인스턴스]
tags: [stp, mst, vlan, layer2]
source: 260121_네트워크_이론_5.pdf
created: 2026-01-21
status: complete
---
# 개념
PVST/RPVST 환경에서 VLAN 수가 많을수록 STP 인스턴스가 늘어나 CPU/RAM 리소스를 낭비하는 문제를 해결하기 위해, 여러 VLAN을 하나의 STP 인스턴스(인스턴스)로 묶어 처리하는 방식.

# 핵심 포인트
- **문제 배경**: PVST에서 VLAN 200개 = STP 인스턴스 200개 → 과도한 리소스 소모
- **MST 해결 방식**: 여러 VLAN을 **인스턴스 단위**로 그룹화 → 같은 토폴로지를 공유하는 VLAN끼리 묶음
  - 예: 인스턴스1 = VLAN 10,20,30 / 인스턴스2 = VLAN 40,50,60
- **주의사항**: MST로 구성된 스위치의 인접 디바이스는 반드시 MST 동작 필요
- **MST 설정 절차**:
  ```
  SW1(config)#spanning-tree mode mst
  SW1(config)#spanning-tree mst configuration
  SW1(config-mst)#name CCNA
  SW1(config-mst)#instance 1 vlan 10,20,30
  SW1(config-mst)#instance 2 vlan 40,50,60
  SW1(config-mst)#exit
  ```
- **인스턴스별 Root Bridge 지정**:
  ```
  SW2(config)#spanning-tree mst 1 priority 4096   (인스턴스 1의 Root = SW2)
  SW3(config)#spanning-tree mst 2 priority 4096   (인스턴스 2의 Root = SW3)
  ```
- `show spanning-tree mst`: MST 인스턴스별 STP 정보 확인

# 나만의 언어로
<!-- 이 개념을 누군가에게 설명한다면? 비유, 요약, 한 줄 정리 등 -->
VLAN이 200개면 STP 반장도 200명? MST는 "비슷한 VLAN끼리 팀을 만들어 팀당 반장 한 명"만 두는 방식. 리소스를 대폭 절약한다.

# 상위 개념
- [[STP PVST & RPVST]]

# 관련 개념
- [[STP]]
- [[VLAN]]
- [[802.1Q Trunk]]
