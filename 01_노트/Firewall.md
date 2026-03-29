---
uid: 202603290901
aliases: [방화벽, Stateful Firewall, Stateless Firewall]
tags: [firewall, security, network]
source: RAPA 참고자료 - 260313_Firewall.pdf
created: 2026-03-29
status: complete
---
# 개념
방화벽(Firewall)은 신뢰할 수 있는 네트워크(LAN)와 신뢰할 수 없는 네트워크(WAN) 사이에서 패킷을 **허용 또는 차단**하는 보안 장비이다.

## Stateless Filtering vs Stateful Filtering

### Stateless Filtering (라우터 ACL)
- Source / Destination / Port Number를 기준으로 개별 패킷을 독립적으로 처리
- 이전에 본 적이 있는 패킷인지 추적하지 않음
- 각 패킷을 매번 ACL에 대조하여 판단

### Stateful Filtering (방화벽)
- 모든 IN/OUT **Connection을 추적**
- 내부에서 외부로 나간 연결을 기억하고, 해당 연결의 응답 트래픽을 **자동 허용**
- 예: TCP 3-Way Handshake 과정을 모니터링하여 세션 상태 관리

## Packet Inspection (Deep Packet Inspection)
- ACL은 L3/L4(IP, Port)만 검사
- 방화벽은 **OSI Layer 7(Application)까지** 검사 가능
  - 애플리케이션 헤더 및 실제 데이터(Payload) 확인
  - IP 차단 대신 **URL 차단** 가능
  - 바이러스, 웜 등 악성 패킷 탐지/차단

## Security Zone
- 라우터: ACL 기반 → 인터페이스마다 ACL 관리 필요 → 복잡
- 방화벽: **Zone 기반** → Security Level로 간편하게 관리

### Zone 구조
| Zone | Security Level | 설명 |
|------|---------------|------|
| INSIDE | High (100) | 내부 LAN 구간 |
| DMZ | Medium (50) | 공개 서버 구간 |
| OUTSIDE | Low (0) | 외부 WAN 구간 |

### Zone 간 트래픽 규칙
- **High → Low**: 기본 허용
- **Low → High**: 기본 거부 (ACL 예외 필요)
- Stateful 동작으로 나가는 연결의 리턴 트래픽은 자동 허용

### DMZ 운영 시 트래픽 흐름
- INSIDE → OUTSIDE: 허용
- INSIDE → DMZ: 허용
- DMZ → OUTSIDE: 허용
- DMZ → INSIDE: 거부
- OUTSIDE → DMZ: 거부 (ACL 예외 필요)
- OUTSIDE → INSIDE: 거부

# 핵심 포인트
- 방화벽은 **Stateful Inspection**으로 연결 상태를 추적하여 ACL보다 정교한 보안 제공
- Layer 7까지 검사 가능 (DPI)
- Zone + Security Level 기반으로 정책을 단순화

# 상위 개념
- [[네트워크 기초]]

# 관련 개념
- [[ACL]]
- [[NAT]]
- [[Firewall CBAC]]
- [[Firewall ZFW]]
- [[ASA]]
