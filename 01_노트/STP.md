---
uid: 202601210903
aliases: [Spanning Tree Protocol, STP, Root Bridge, BPDU, Bridge ID, 루프 방지]
tags: [stp, switch, layer2, loop-prevention]
source: 260121_네트워크_이론_5.pdf
created: 2026-01-21
status: complete
---
# 개념
스위치 이중화 구성 시 발생하는 물리적 루프를 방지하는 프로토콜. 특정 포트를 차단(Blocking)하여 루프 없는 논리적 토폴로지를 제공한다.

# 핵심 포인트
- **STP가 필요한 이유**: 이중화를 위해 스위치 간 루프 구조 필요 ↔ 루프 발생 시 Broadcast Storm 등 심각한 문제 발생
- **BPDU (Bridge Protocol Data Unit)**: STP가 동작하는 스위치 간 교환하는 프레임
  - BPDU에 포함되는 **Bridge ID** = Priority + MAC Address (System ID)
- **Root Bridge 선출 과정**
  1. 모든 스위치가 BPDU 교환
  2. **가장 낮은 Bridge ID**를 가진 스위치가 Root Bridge로 선출
  3. 기본 Priority = **32768** (낮을수록 우선, 동일 시 낮은 MAC이 우선)
- **포트 역할 (Port Role)**
  - **Root Port**: Non-Root Bridge에서 Root Bridge로 가는 가장 짧은 경로(Cost)를 갖는 포트
  - **Designated Port**: 각 세그먼트에서 Root Bridge 쪽으로 데이터를 전달하는 포트 (Root Bridge의 모든 포트)
  - **Alternate Port (BLK)**: 루프 방지를 위해 차단된 포트 → 더 높은 BID를 가진 스위치가 Block
- **포트 상태 전환 (Port States)**
  - **Listening** (15sec): BPDU 송수신, MAC 학습 불가, 데이터 전송 불가
  - **Learning** (15sec): BPDU 송수신, MAC 학습, 데이터 전송 불가
  - **Forwarding**: 데이터 전송 가능 (최종 상태)
  - **Blocking**: 루프 방지를 위해 데이터 차단 (BPDU 수신만 가능)
  - 최초 연결 시 Forwarding까지 **30초** 소요 (Listening 15 + Learning 15)
  - Blocking → Forwarding 전환 시 **50초** 소요 (Max Age 20 + 30초)
- `show spanning-tree`: STP 동작 상태 확인 (Root Bridge 정보, 포트 역할/상태, Cost, Priority)
- **STP 타이머**
  - Hello Time: 2sec (BPDU 전송 주기)
  - Max Age: 20sec (BPDU 미수신 시 최대 대기 시간)
  - Forward Delay: 15sec (Listening, Learning 각각 유지 시간)

# 나만의 언어로
<!-- 이 개념을 누군가에게 설명한다면? 비유, 요약, 한 줄 정리 등 -->
스위치 이중화 = 루프 위험. STP는 "나쁜 경로"를 하나 막아(BLK) 루프를 없앤다. Root Bridge는 반장 역할, 모든 경로는 반장 기준으로 결정된다.

# 상위 개념
- [[LAN Switching]]

# 관련 개념
- [[STP PVST & RPVST]]
- [[STP MST]]
- [[STP Tuning (PortFast, RootGuard, BPDU Guard)]]
- [[802.1Q Trunk]]
