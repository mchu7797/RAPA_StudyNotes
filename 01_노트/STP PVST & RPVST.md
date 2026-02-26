---
uid: 202601210904
aliases: [PVST, RPVST, Per-VLAN STP, Rapid PVST, Rapid Spanning Tree]
tags: [stp, pvst, rpvst, vlan, layer2]
source: 260121_네트워크_이론_5.pdf
created: 2026-01-21
status: complete
---
# 개념
PVST는 VLAN별로 독립적인 STP 인스턴스를 실행하는 Cisco 구현 방식. RPVST는 수렴 속도를 개선한 진화형이다.

# 핵심 포인트
- **PVST (Per-VLAN Spanning Tree)**
  - IEEE 802.1D 기반, Cisco 전용
  - VLAN별 독립된 STP 인스턴스 실행 → VLAN마다 다른 Root Bridge 지정 가능
  - **부하 분산(Load Balancing)** 가능: VLAN 10의 Root = SW1, VLAN 20의 Root = SW2
  - 비효율적 운영: 모든 VLAN이 동일한 Root Bridge를 사용하면 링크 낭비
  - Priority = 32768 + VLAN ID (sys-id-ext)
- **RPVST (Rapid PVST, 802.1w 기반)**
  - EIGRP, OSPF와 같은 라우팅 프로토콜 수렴 속도에 맞추기 위해 개발
  - PVST보다 **훨씬 빠른 수렴** (토폴로지 변화에 즉각 대응)
  - Port State 단순화:
    | PVST | RPVST | MAC 학습 |
    |------|-------|---------|
    | Blocking | Discarding | No |
    | Listening | Discarding | No |
    | Learning | Learning | Yes |
    | Forwarding | Forwarding | Yes |
  - Root Bridge 결정 방식은 PVST와 동일
- **RPVST 설정**:
  ```
  SW1(config)#spanning-tree mode rapid-pvst
  ```
- `show spanning-tree`: `protocol ieee` = PVST, `protocol rstp` = RPVST 확인
- Root Bridge 지정 (Priority 낮게 설정):
  ```
  SW1(config)#spanning-tree vlan [VLAN-ID] priority 4096
  ```

# 나만의 언어로
<!-- 이 개념을 누군가에게 설명한다면? 비유, 요약, 한 줄 정리 등 -->
PVST = VLAN마다 STP 반장을 따로 뽑아 트래픽을 분산. RPVST = 같은 방식이지만 반장이 바뀔 때 훨씬 빨리 새 반장이 정해진다.

# 상위 개념
- [[STP]]

# 관련 개념
- [[VLAN]]
- [[STP MST]]
- [[STP Tuning (PortFast, RootGuard, BPDU Guard)]]
