---
uid: 202602251335
aliases: [LSA Type]
tags: [network, routing, ospf, lsa]
source: RAPA 수업 (2/25)
created: 2026-02-25
status: complete
---
# 개념

## Type 1 : Router LSA
- 동일 Area 내에서 Flood되는 LSA
- Connected Network를 포함하고 있음.
## Type 2 : Network LSA
- Multi-Access  환경에서 선출된 DR에 의해 생성
- DR의 Sub Netmask와 DR에 연결된 라우터 목록을 포함
- 동일안 Area 내에서 Flooding
## Type 3: Summary LSA (Code: O IA)
- ABR(Area Border Router)에 의해 생성되는 LSA
- 다른 Area에 전달하는 LSA
- 이름은 Summary지만 무조건 요약된 내용은 아닐 수 있음
	- 요약이 불가능하다는 것이 아니라 안하는 경우도 있다는 것
## Type 4 : Summary ASBR LSA
- 다른 라우팅 프로토콜 또는 정적 라우팅 정보를 OSPF Area 내부로 전파해야 하는 ASBR의 정보를 같은 Area의 ABR이 받아 다른 Area로 전파되는 LSA
- ASBR은 동일한 Area 내부에 Type-1 또는 Type-2 LSA를 전파함. 이를 수신한 다른 ABR 라우터는 Type-4로 변경한 뒤 전파함.
- OSPF의 모든 라우터는 Type-4 LSA를 통해 ASBR 위치를 알게 됨.
## Type 5 : External LSA (Code: O E1, O E2)
- ASBR에 의해 외부 경로가 OSPF 내부로 전파된 경로를 포함한 LSA
- 다른 라우터는 Type-4를 통해 ASBR Router를 학습한 상태여야 함.
# 핵심 포인트
|**LSA Type**|**이름**|**핵심 내용 및 역할**|**경로 정보(IP/Mask) 포함 여부**|
|---|---|---|---|
|**Type 1**|**Router LSA**|**자기 자신의 신분증.** 모든 OSPF 라우터가 생성하며, 인접한 장비와 자신의 인터페이스 상태를 알림.|**포함**|
|**Type 2**|**Network LSA**|**반장의 출석부.** Multi-Access(스위치) 구간에서 DR이 생성. 누가 연결되어 있는지 큰 그림을 그려 복잡도를 줄임.|**미포함** (서브넷 마스크만 보조)|
|**Type 3**|**Summary LSA**|**옆 동네 소식지.** ABR이 생성. 다른 Area의 상세 지도를 숨기고 "이 IP 대역은 나를 거쳐라"라고 알려줌.|**포함**|
|**Type 4**|**ASBR Summary**|**ASBR 수배 전단지.** ABR이 생성. 외부로 나가는 통로(ASBR)가 어디 있는지 위치(Router-ID)만 알려줌.|**미포함**|
|**Type 5**|**External LSA**|**외국 뉴스.** ASBR이 생성. 외부 프로토콜(RIP, EIGRP 등)에서 가져온 경로 정보를 OSPF 전체에 뿌림.|**포함**
# 상위 개념
- [[OSPF]]
# 관련 개념
- [[OSPF LSA Priority]]
- [[Redistribute]]
