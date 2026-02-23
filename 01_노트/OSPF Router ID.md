# 개념
- [[OSPF]]는 효율적인 운영 환경을 위해 고유한 Router ID가 필요함. (IP 주소 형식)
	1. [[OSPF]]설정 과정에서 운영자가 직접 입력
	2. [[OSPF]]는 라우터의 Loopback IP를 Router ID로 사용
		- 라우터의 Loopback 인터페이스가 여러 개 있을 경우, Loopback 중 가장 높은 IP를 Router ID로 사용
	3. 라우터에 Loopback 인터페이스가 없는 경우, 물리적 인터페이스의 가장 높은 IP를 Router ID로 사용
- [[OSPF Neighbor]] 협상 과정에서 결정된 Router ID는 변경 불가
	- Router ID 변경을 위해서는 [[OSPF Neighbor]] 재협상이 필요함.
![[ospf_router_id.png]]
# 상위 개념
- [[OSPF Neighbor]]
- [[OSPF]]