---
uid: 202601210906
aliases: [PortFast, RootGuard, BPDU Guard, BPDU Filter, LoopGuard, STP Tuning, STP 최적화]
tags: [stp, portfast, rootguard, bpduguard, bpdufilter, loopguard, layer2, security]
source: 260121_네트워크_이론_5.pdf
created: 2026-01-21
status: complete
---
# 개념
STP의 동작을 최적화하거나 토폴로지를 보호하기 위한 기능들. 주로 엣지 포트 빠른 전환과 불필요한 Root Bridge 변경 방지에 사용된다.

# 핵심 포인트
- **PortFast** (Cisco 전용)
  - 호스트 연결 포트에서 Listening/Learning 단계를 생략하고 즉시 Forwarding 전환
  - 토폴로지 변경 알림(TCN) 생성 안 함 → 불필요한 MAC 테이블 플러시 방지
  - **주의**: 스위치/허브 연결 포트에는 절대 사용 금지 (루프 위험)
  - 설정:
    ```
    SW1(config-if)#spanning-tree portfast
    ```
- **RootGuard**
  - 특정 포트에서 현재 Root Bridge보다 **더 좋은 BID를 가진 BPDU를 수신하면 해당 포트를 차단**
  - 의도치 않은 Root Bridge 변경(토폴로지 혼란) 방지
  - 설정:
    ```
    SW2(config-if)#spanning-tree guard root
    ```
- **BPDU Guard**
  - 원하지 않는 포트로 **BPDU가 수신되면 해당 포트를 즉시 err-disable 상태로 차단**
  - PortFast 활성화 포트(호스트 연결 포트)에 함께 사용 권장
  - 무단 스위치 연결로 인한 STP 토폴로지 변경 방지
  - 설정:
    ```
    SW2(config-if)#spanning-tree bpduguard enable
    ```

- **BPDU Filter**
  - BPDU 송수신을 차단하는 기술 (BPDU Guard와 유사하지만 동작 방식 다름)
  - **Global 설정**: PortFast 활성화 포트에만 동작. BPDU 수신 시 PortFast 해제 + Filter 비활성화
  - **Interface 설정**: 해당 포트의 BPDU 송/수신 완전 중지 → 스위치 연결 포트에 설정 시 **루프 발생 주의**
  - 설정: `spanning-tree bpdufilter enable`
- **LoopGuard**
  - 케이블 장애로 인한 **단방향 링크** 또는 H/W 오동작으로 BPDU를 못 받는 경우, 해당 포트가 Forwarding으로 전환되어 루프가 생기는 것을 방지
  - BPDU 미수신 포트를 Loop-Inconsistent 상태로 차단
  - 설정: `spanning-tree loopguard default` (글로벌)

- PortFast: PC 연결 포트에서 30초 대기를 없애 즉시 통신 가능하게 함
- RootGuard: "이 포트로는 새 반장 후보를 받지 않겠다"
- BPDU Guard: "이 포트로 BPDU가 오면 즉시 차단 (무단 스위치 연결 차단)"

# 상위 개념
- [[STP]]

# 관련 개념
- [[STP PVST & RPVST]]
- [[LAN Switching]]
- [[스위치 기본 설정]]
