---
uid: 202602230026
aliases: [LSU]
tags: [network, routing, ospf, link-state]
source: RAPA 수업 (2/23)
created: 2026-02-23
status: complete
---
# 개념
- 상대방이 요청한 정보를 실제로 보내주거나, 네트워크에 변화가 생겼을 때, 정보를 업데이트하기 위해 사용하는 패킷
- [[OSPF]]에서 가장 핵심적인 패킷으로, 이 안에 실제 경로 정보인 [[Link-State Advertisements (LSA)|LSA]]가 실려서 전달됨.
- 라우팅 테이블이 만들어지는 실질적인 데이터가 이 안에 들어있음.
# 상위 개념
- [[OSPF Neighbor]]
- [[OSPF]]
# 관련 개념
- [[Link-State Acknowledge (LSAck)]]
- [[Link-State Advertisements (LSA)]]
- [[Link-State Description (LSD)]]
- [[Link-State Database (LSDB)]]