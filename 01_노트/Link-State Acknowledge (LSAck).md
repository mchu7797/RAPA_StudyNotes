---
uid: 202602230023
aliases: [LSAck]
tags: [network, routing, ospf, link-state]
source: RAPA 수업 (2/23)
created: 2026-02-23
status: complete
---
# 개념
- [[OSPF]]는 신뢰성이 중요한 프로토콜로, 정보를 받았다면 잘 받았다고 대답해줘야함.
- [[Link-State Update (LSU)|LSU]] 패킷을 수신했을 때, 정보를 잘 받았다고 회신하는 역할을 하는 패킷임.
- 일정 시간동안 [[Link-State Acknowledge (LSAck)|LSAck]]이 오지 않으면, 라우터는 상대방이 못 받은 줄 알고 [[Link-State Update (LSU)|LSU]]를 다시 보냄.
# 나만의 언어로

# 상위 개념
- [[OSPF Neighbor]]
- [[OSPF]]
# 관련 개념
- [[Link-State Update (LSU)]]
- [[Link-State Description (LSD)]]
- [[Link-State Advertisements (LSA)]]