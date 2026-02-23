# 개념
- [[Link-State Advertisements (LSA)]]란, OSPF의 패킷 중 하나로, 자신의 주변 네트워크 연결 상태를 (Link and State) 다른 라우터들에게 알리기 위해 사용하는 정보 패킷
- 이름과 같이 **광고**를 하기 위한 패킷이다.
- 하나의 독립적인 패킷이라기보다는, [[Link-State Description (LSD)]]  패킷 중 하나의 역할이라고 봐야 한다.
# 전송하는 데이터
- Router ID
- Neighbor
- Cost/Metric
# 상위 개념
- [[OSPF]]
# 연관 개념
- [[Link-State Database (LSDB)]]
- [[Link-State Description (LSD)]]
- [[Link-State Update (LSU)]]
- [[Link-State Acknowledge (LSAck)]]