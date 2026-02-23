# 개념
- Link-State 정보를 주고받기 위해서는 인접 장비와 Neighbor 관계 형성이 필요함
	- [[OSPF]]를 구성하면 라우터는 [[OSPF]]가 활성화된 인터페이스로 Hello 패킷을 송신함.
	- 이때 Hello패킷은 멀티캐스트 형태로 전송된다. (224.0.0.5)
- Hello Packet 정보 중 몇 가지는 반드시 일치해야 Neighbor 관계를 형성 가능함.
# 하위 개념
- [[Neighbor 관계 형성 조건]]
- [[OSPF Neighbor 관계 수립 과정]]
# 프로토콜 개념
- [[Link-State Advertisements (LSA)]]
- [[Link-State Database (LSDB)]]
- [[Link-State Update (LSU)]]
- [[Link-State Acknowledge (LSAck)]]
# 상위 개념
- [[OSPF]]