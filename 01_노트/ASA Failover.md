---
uid: 202603290907
aliases: [ASA Failover, Active Standby Failover, ASA HA]
tags: [firewall, security, asa, failover, ha]
source: RAPA 참고자료 - 260313_Firewall.pdf
created: 2026-03-29
status: complete
---
# 개념
ASA는 VPN, NAT, Filtering 등 중요한 보안 기능을 담당하므로, 장애 대비를 위한 **이중화(Active/Standby Failover)**를 지원한다. 평소 Active 장비가 동작하고, Active 장애 시 Standby가 자동으로 역할을 인수한다.

## Failover 조건
- **동일한 플랫폼** (예: 2 x ASA5510)
- 하드웨어 스펙 동일 (인터페이스 수/종류, 플래시, RAM)
- **동작 모드 동일** (L2 또는 L3)
- **라이선스 종류 동일** (VPN Peer 수, 암호화 지원 등)

## 구성 요소
| 요소 | 설명 |
|------|------|
| **Failover Link** | 장비 간 상태 체크 및 설정 동기화 |
| **State Link** | Stateful 연결 정보 동기화 |
| **Active** | 실제 트래픽 처리 장비 |
| **Standby** | 대기 장비. Active 설정이 자동 동기화 |

- Failover Link와 State Link를 **동일 인터페이스로** 사용 가능

## 설정 순서

### Primary (Active) 장비
```bash
! 1) Primary 지정
failover lan unit primary

! 2) Failover 인터페이스 구성
failover lan interface FAILOVER Ethernet 0/3
failover link FAILOVER Ethernet 0/3
failover interface ip FAILOVER 192.168.12.1 255.255.255.0 standby 192.168.12.2

! 3) Failover 활성화
failover

! 4) 데이터 인터페이스 설정 (standby IP 포함)
interface Ethernet 0/0
 nameif INSIDE
 ip address 192.168.1.254 255.255.255.0 standby 192.168.1.253
 no shutdown

interface Ethernet 0/1
 nameif OUTSIDE
 ip address 192.168.2.254 255.255.255.0 standby 192.168.2.253
 no shutdown
```

### Secondary (Standby) 장비
```bash
failover lan unit secondary
failover lan interface FAILOVER Ethernet 0/3
failover link FAILOVER Ethernet 0/3
failover interface ip FAILOVER 192.168.12.1 255.255.255.0 standby 192.168.12.2
failover
```

## 동작 특성
- Failover 구성 후 **모든 설정은 Active 장비에서** 진행
- Standby 장비는 Active의 설정이 **자동 동기화**
- `write memory` 시 양쪽 모두에 저장
- Stateful 세션 정보도 동기화 → 장애 시 기존 연결 유지

## 확인 명령어
- `show failover` - Failover 상태, Unit 역할, 인터페이스 상태
- `show failover state` - Active/Standby 상태 요약

# 핵심 포인트
- ASA Failover는 **Active/Standby** 구조로 고가용성 보장
- 설정 및 Stateful 세션 정보가 자동 동기화
- 반드시 **동일 하드웨어/라이선스/모드** 조건 충족 필요

# 상위 개념
- [[ASA]]

# 관련 개념
- [[Gateway Redundancy (HSRP, VRRP)]]
- [[Firewall]]
