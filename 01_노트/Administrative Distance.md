---
uid: 202602230009
aliases: [AD]
tags: [network, routing, administrative-distance]
source: RAPA 수업 (2/23)
created: 2026-02-23
status: complete
---
# 개념
Administrative Distance(AD)는 **라우터가 여러 라우팅 프로토콜로부터 동일한 목적지 경로를 학습했을 때, 어느 프로토콜의 정보를 신뢰할지 결정하는 기준값**이다. 값이 낮을수록 신뢰도가 높으며, 라우팅 테이블에 우선 등록된다.

- 라우터 로컬 값 → 다른 라우터에게 전달되지 않음
- 벤더마다 기본값이 다를 수 있음 (아래는 Cisco 기준)

## AD 값 표

| 소스 | AD 값 |
|------|-------|
| Directly Connected | **0** |
| Static Route | **1** |
| EIGRP Summary | 5 |
| External BGP (eBGP) | 20 |
| EIGRP | **90** |
| OSPF | **110** |
| IS-IS | 115 |
| RIP | **120** |
| External EIGRP | 170 |
| Internal BGP (iBGP) | 200 |
| Unknown / 사용 불가 | 255 |

## 동작 예시
- OSPF(AD 110)와 EIGRP(AD 90)가 동일 목적지 경로를 광고 → **EIGRP 경로가 라우팅 테이블에 등록**
- Static Route(AD 1)는 거의 모든 동적 라우팅 프로토콜보다 우선

# 핵심 포인트
- AD는 **프로토콜 간 비교** 기준 (같은 프로토콜 내 비교는 [[Administrative Distance & Metric|Metric]] 사용)
- Best Path 선출 순서: **AD → Metric → Longest Match**
- AD 255는 라우팅 테이블에 등록 불가

# 상위 개념
- [[IP 라우팅]]

# 관련 개념
- [[Administrative Distance & Metric]]
- [[Static Routing]]
- [[Dynamic Routing]]
- [[Dynamic Routing Protocol]]
- [[EGP]]
- [[EIGRP]]
- [[OSPF]]
