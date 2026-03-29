---
uid: 202602250902
aliases: [재분배, 경로 재분배]
tags: [network, routing, redistribute]
source: RAPA 수업 (2/25)
created: 2026-02-25
status: complete
---
# 개념
- 서로 다른 라우팅 프로토콜 간에 경로를 전달하기 위해 사용하는 기능
- Connected, Static을 포함한 모든 경로를 재분배할 수 있음
- 재분배를 수행하는 라우터는 두 개 이상의 라우팅 프로토콜이 동작하는 경계 라우터임
# 프로토콜별 재분배 특성

## OSPF에서의 재분배
- ASBR (Autonomous System Boundary Router)에 의해 재분배가 발생함
- 재분배된 경로는 `O E2` 또는 `O E1` 코드를 가지고 라우팅 테이블에 등록됨
	- 기본값은 `O E2`
- 다른 프로토콜의 경로를 OSPF로 재분배 시 반드시 `subnets` 옵션을 적용해야 함
```
router ospf 1
 redistribute rip subnets
 redistribute eigrp 1 subnets
 redistribute static subnets
 redistribute connected subnets
```
- metric-type 옵션으로 E1 / E2를 지정할 수 있음
```
redistribute connected subnets metric-type 1   ! O E1
redistribute connected subnets metric-type 2   ! O E2 (기본값)
redistribute connected subnets                 ! O E2 (기본값)
```

## EIGRP에서의 재분배
- 재분배된 경로는 `D EX` 코드를 가지며, AD 값은 170임
- Seed Metric을 반드시 지정해야 함 (bandwidth, delay, reliability, load, MTU)
```
router eigrp 1
 redistribute ospf 1 metric 1 1 1 1 1
```

## RIP에서의 재분배
- Seed Metric으로 Hop Count를 지정함
```
router rip
 redistribute ospf 1 metric 1
```
# O E1 vs O E2
| 구분 | O E1 | O E2 |
|---|---|---|
| **Cost 계산** | 외부 Metric + 내부 Cost (변동) | 외부 Metric만 사용 (고정) |
| **Hop 증가 시** | Cost 증가됨 | Cost 증가되지 않음 |
| **기본값** | - | ✅ (Default) |
| **metric-type** | 1 | 2 (또는 생략) |
# 핵심 포인트
- OSPF에서 재분배 설정을 하는 순간 해당 라우터는 ASBR로 선언됨
- Static 경로를 재분배하는 경우, 상대측에 Return Traffic을 위한 정적 경로가 필요할 수 있음
- 재분배 시 Seed Metric 설정을 잊지 말 것 (프로토콜마다 Metric 체계가 다름)
# 상위 개념
- [[Dynamic Routing]]
# 관련 개념
- [[OSPF]]
- [[EIGRP]]
- [[OSPF LSA Priority]]
- [[OSPF Area]]
