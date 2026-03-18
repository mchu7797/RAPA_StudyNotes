---
uid: 202603040844
aliases: [BGP Adjacency States, BGP Neighbor State]
tags: [network, routing, bgp, neighbor]
source: RAPA 수업 (3/3) - 네트워크 이론 9
created: 2026-03-04
status: draft
---
# 개념
BGP Neighbor 관계는 TCP 3-way Handshake 위에서 동작하며, 총 6단계 상태를 거쳐 Established 상태가 된다.

| 상태 | 설명 |
|------|------|
| **Idle** | 초기 상태. BGP 프로세스가 TCP 연결을 시도하기 전 대기 상태 |
| **Connect** | TCP 연결을 시도 중인 상태 |
| **Active** | TCP 연결 실패 후 재시도 중인 상태. Neighbor IP가 잘못됐거나 도달 불가인 경우 여기서 머뭄 |
| **OpenSent** | TCP 연결 성공 후 OPEN 메시지를 전송한 상태. 상대방의 OPEN 메시지를 기다리는 중 |
| **OpenConfirm** | OPEN 메시지를 주고받은 후 KEEPALIVE 또는 NOTIFICATION을 기다리는 상태 |
| **Established** | BGP 세션이 완전히 수립된 상태. UPDATE 메시지로 라우팅 정보를 교환 |

## 상태 흐름
```
Idle → Connect → OpenSent → OpenConfirm → Established
           ↓
         Active (TCP 실패 시)
```

## 트러블슈팅 포인트
- **Active 상태에서 멈춤** : Neighbor IP 설정 오류, 물리적 연결 문제, ACL 차단 (TCP 179)
- **OpenSent에서 멈춤** : AS 번호 불일치, BGP 버전 불일치, Authentication 설정 불일치

## 디버그 명령어
```
# debug ip bgp
show ip bgp neighbors
show ip bgp summary
```

# 핵심 포인트
- **Active 상태** = 아직 연결 안 됨. "Active하게 시도 중"이라는 의미이지 정상 상태가 아님.
- **Established** = 정상 동작 상태. 이 상태에서만 라우팅 정보(UPDATE)를 교환한다.
- Hold Time : 기본 180초, 이 시간 내에 KEEPALIVE가 없으면 세션 종료

# 나만의 언어로
<!-- 이 개념을 누군가에게 설명한다면? 비유, 요약, 한 줄 정리 등 -->

# 상위 개념
- [[BGP]]

# 관련 개념
- [[BGP 메시지 타입]]
- [[BGP eBGP & iBGP]]
