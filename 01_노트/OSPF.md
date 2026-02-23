# 개념
- 각 라우터는 자신과 자신의 인터페이스(Link-State) 정보를 인접 라우터에게 수집하고 광고함.
	- 이 정보는 한 라우터에서 다른 라우터로 변경되지 않고 전달함.
	- Network 정보를 받으면 Ack 메시지를 통해 정상 전달 확인.
- 네트워크 토폴로지 정보를 모든 라우터에게 전달해 전체 그림을 학습 후 동시에 라우팅 테이블 생성.
- 단, Network 크기에 비례해 라우팅 테이블 계싼에 사용되는 하드웨어 리소스가 늘어날 수 있음.
- 표준 라우팅 프로토콜이자, TCP/IP 환경에서 가장 많이 사용되는 라우팅 프로토콜
- 지도의 크기를 조절하기 위해 Area 단위로 나눠 운영함.
# Link-State
- Link : 라우터의 인터페이스
- State : 인터페이스에 연결된 인접 라우터의 연결 상태
# 핵심 포인트 
- [[OSPF]]는 Link-State 기반 라우팅 프로토콜에 속함.
- 여기서 핵심은, 모든 라우터는 정해진 구역 내의 모든 네트워크 정보를 가지고 있다는 점임. 구조적으로 Loop이 불가능한 형태이기도 함.
- 이로 인해 생기는 단점이 있는데, 네트워크 구조가 커질수록 연산 시간이 늘어남.
	- 단 현재는 기술의 발전으로 인해 크게 체감되지 않음.
# 하위 개념
- [[Link-State Advertisements (LSA)]]
- [[Link-State Database (LSDB)]]
- [[SPF Algorithm]]
- [[OSPF Area]]
- [[OSPF Neighbor]]
- [[OSPF Router ID]]
- [[OSPF Metric]]
- [[OSPF Passive Interface]]
- [[OSPF DR, BDR]]
# 사용 방법
- [[OSPF 기본 설정]]
# 관련 개념
- [[IGP]]
- [[Dynamic Routing]]
- [[Dynamic Routing Protocol]]
- [[EIGRP]]