---
uid: 202602230021
aliases: [OSPF Neighbor 상태]
tags: [network, routing, ospf, neighbor]
source: RAPA 수업 (2/23)
created: 2026-02-23
status: complete
---
![[ospf_neighbor_connection.png]]
# DOWN
* Hello Packet 미수신
* Deadtime 동안 Hello Packet 미수신
* 인접 장비와 비정상 연결
# Init
* 단방향 Hello Packet 수신 상태
# 2-way
* Neighbor 장비와 쌍방 통신이 이뤄진 상태
# Exchange
* OSPF 설정된 장비들이 DBD 를 교환하는 단계
# Loading
* DBD 수신 후 필요에 따라 LSR, LSU, LSAck 교환하는 단계
# Full
* Neighbor 장비들간 라우팅 정보교환이 끝난 상태
# 나만의 언어로

# 상위 개념
- [[OSPF Neighbor]]