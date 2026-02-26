---
uid: 202601210910
aliases: [HSRP, VRRP, Gateway Redundancy, 게이트웨이 이중화, 가상 게이트웨이, Hot Standby]
tags: [hsrp, vrrp, redundancy, gateway, layer3, high-availability]
source: 260121_네트워크_이론_5.pdf
created: 2026-01-21
status: complete
---
# 개념
호스트의 Default Gateway 역할을 하는 장비에 장애가 발생해도 통신이 끊기지 않도록 가상 게이트웨이를 구성하는 기술.

# 핵심 포인트
- **문제 배경**: 호스트는 단 하나의 Default GW IP만 설정 가능 → 해당 장비 장애 시 통신 단절
- **해결책**: 두 L3 스위치가 **가상 IP + 가상 MAC**을 공유, 한 대만 실제 패킷 처리 → 장애 시 자동 전환

---

### HSRP (Hot Standby Router Protocol) — Cisco 전용
- **Active**: 실제로 패킷 처리, 가상 GW IP + vMAC 보유
- **Standby**: Active 감시, 장애 시 Active로 전환
- **가상 MAC**: `0000.0c07.acXX` (XX = HSRP Group Number)
- **상태 전환**: Initial → Listen → Speak → Standby → Active
- **Priority**: 높을수록 Active 우선 (기본값 100), 동일 시 높은 IP가 Active
- **Preempt**: 운영 중 Priority 높은 장비가 Active를 빼앗아 올 수 있도록 설정 필요
  ```
  SW1(config-if)#standby 1 ip 192.168.1.254      (가상 GW IP)
  SW1(config-if)#standby 1 priority 150           (Priority 높게)
  SW1(config-if)#standby 1 preempt                (Preempt 활성)
  ```
- **HSRPv1 vs v2**: v2는 그룹 번호 0~4095, 멀티캐스트 224.0.0.102, vMAC `0000.0c9f.fXXX`

---

### VRRP (Virtual Router Redundancy Protocol) — IEEE 표준 (RFC 3768)
- **Master**: 실제 패킷 처리 (HSRP Active에 해당)
- **Backup**: Master 감시 및 대기
- **가상 MAC**: `0000.5e00.01XX` (XX = group number)
- **Preempt 기본 활성화** (HSRP와 다름)
- 가상 IP = 실제 인터페이스 IP와 동일하게 설정 가능
  ```
  SW1(config-if)#vrrp 1 ip 192.168.1.3
  SW1(config-if)#vrrp 1 priority 150
  ```

---

### HSRP vs VRRP 비교

| 항목 | HSRP | VRRP |
|------|------|------|
| 표준 | Cisco 전용 | IEEE (RFC 3768) |
| 역할 명칭 | Active / Standby | Master / Backup |
| Preempt 기본값 | 비활성 | **활성** |
| 멀티캐스트 | 224.0.0.2 (v1) / 224.0.0.102 (v2) | 224.0.0.18 |
| Hello/Hold 타이머 | 3sec / 10sec | 1sec / 3sec |

# 나만의 언어로
<!-- 이 개념을 누군가에게 설명한다면? 비유, 요약, 한 줄 정리 등 -->
두 개의 라우터가 "하나인 척" 하나의 IP를 공유. 실제 일하는 건 Active(Master) 하나지만, 쓰러지면 즉시 Standby(Backup)가 대신한다. 호스트 입장에서는 GW가 바뀐 줄 모른다.

# 상위 개념
- [[Multi-Layer Switch]]

# 관련 개념
- [[Default Gateway]]
- [[Network Design (Campus)]]
- [[IP 라우팅]]
