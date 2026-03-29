---
uid: 202602230005
aliases: [Interior Gateway Protocol]
tags: [network, routing, routing-protocol, igp]
source: RAPA 수업 (2/23)
created: 2026-02-23
status: complete
---
# 개념
IGP(Interior Gateway Protocol)는 **단일 AS(Autonomous System) 내부**에서 라우터 간 경로 정보를 교환하기 위한 라우팅 프로토콜이다. 조직 내부 네트워크의 빠른 컨버전스와 최적 경로 선출을 목적으로 한다.

## IGP의 두 가지 방식

### Distance Vector
- 인접 라우터에게 라우팅 테이블을 주기적으로 전달
- 전체 토폴로지는 알 수 없고 **방향(Next-Hop)과 거리(Metric)** 만 파악
- 컨버전스 느림, 단순한 환경에 적합
- 예: **RIP**(Hop Count), **EIGRP**(복합 메트릭)

### Link State
- 자신의 링크 상태 정보(LSA)를 네트워크 전체에 플러딩
- 모든 라우터가 **동일한 전체 토폴로지**를 파악 → SPF 알고리즘으로 최적 경로 계산
- 컨버전스 빠름, CPU/메모리 소비 많음
- 예: **OSPF**(Cost), **IS-IS**

## 주요 IGP 비교

| 프로토콜 | 방식 | Metric | AD | 특징 |
|---------|------|--------|----|------|
| **RIP** | Distance Vector | Hop Count | 120 | 단순, 소규모 |
| **EIGRP** | Distance Vector | 복합 메트릭 | 90 | Cisco 계열, 빠른 컨버전스 |
| **OSPF** | Link State | Cost | 110 | 표준 프로토콜, 대규모 적합 |
| **IS-IS** | Link State | Cost | 115 | ISP 환경에서 주로 사용 |

# 핵심 포인트
- IGP는 **단일 AS 내부** 라우팅 전담 (AS 간은 [[EGP]])
- Distance Vector는 단순하지만 컨버전스 느림 / Link State는 빠르지만 리소스 소비
- 대부분의 기업 환경에서 **OSPF** 또는 **EIGRP** 사용

# 하위 개념
- [[OSPF]]
- [[EIGRP]]

# 관련 개념
- [[Dynamic Routing Protocol]]
- [[Dynamic Routing]]
- [[EGP]]
