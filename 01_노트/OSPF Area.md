---
uid: 202602230012
aliases: [OSPF 영역, ABR, ASBR]
tags: [network, routing, ospf]
source: RAPA 수업 (2/23)
created: 2026-02-23
status: complete
---
# 개념
- [[OSPF]]는 Area 개념과 같이 동작함. 
	- 단일 영역 환경에서는 기본적으로 Area 0에서 동작
- [[OSPF]]는 여러 Area를 가지고 동작할 수 있지만, 모든 영역은 Backbone Area(Area 0)에 연결되어야 함.
	- Area 간 통신은 항상 Backbone Area를 통과해야 가능함.
# 명칭 구분

## Backbone Router
- Backbone Area(Area 0)에서 동작하는 라우터
- 잘 사용하지 않는 표현
## Area Border Router (ABR)
- 두 개 이상의 Area에 연결된 라우터.
- 무조건 Backbone Area와 연결되어 있어야 함.
## Autonomous System Border Router (ASBR)
- OSPF와 다른 Routing Protocol을 함께 운영하는 라우터
# 참고 사진
## 싱글 토폴로지
![[ospf_single_area.png]]
## 멀티 토폴로지
![[ospf_multiple_area.png]]
# 나만의 언어로

# 상위 개념
- [[OSPF]]
# 관련 개념
- [[OSPF Multi Process]]
- [[Redistribute]]