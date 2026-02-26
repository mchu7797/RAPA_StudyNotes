---
uid: 202602250901
aliases: [OSPF 멀티 프로세스]
tags: [network, routing, ospf]
source: RAPA 수업 (2/25)
created: 2026-02-25
status: complete
---
# 개념
- 하나의 라우터에서 2개 이상의 OSPF Process를 동작시키는 것
- 각 Process는 독립된 LSDB(지도)를 보유하며, 서로 다른 네트워크 영역을 관리함
- Process 간에는 경로가 자동으로 전달되지 않음
	- 필요 시 [[Redistribute]]를 통해 경로를 전달해야 함
- 2개의 Process는 같은 Router ID를 가질 수 없음
# 설정 예시
```
router ospf 1
 router-id 1.1.1.1
 network 192.168.12.0 0.0.0.255 area 0

router ospf 2
 router-id 11.11.11.11
 network 192.168.23.0 0.0.0.255 area 0
```
# 핵심 포인트
- Multi Area와 혼동하지 말 것
	- Multi Area: 하나의 OSPF Process 내에서 여러 Area로 나누어 운영
	- Multi Process: 완전히 독립적인 OSPF Process를 여러 개 운영
- Process 간 경로 공유가 필요하면 반드시 재분배 설정이 필요함
# 나만의 언어로

# 상위 개념
- [[OSPF]]
# 관련 개념
- [[OSPF Area]]
- [[Redistribute]]
