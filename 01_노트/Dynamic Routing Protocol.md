---
uid: 202602230003
aliases: [동적 라우팅 프로토콜]
tags: [network, routing, dynamic-routing]
source: RAPA 수업 (2/23)
created: 2026-02-23
status: complete
---
# 개념
라우터들이 서로 경로 정보를 자동으로 교환하기 위해 사용하는 프로토콜. 네트워크 변화를 감지하고 최적 경로를 자동으로 재계산한다.

## 분류 체계

```
Dynamic Routing Protocol
├── IGP (조직 내부 / 단일 AS)
│   ├── Distance Vector: RIP, EIGRP
│   └── Link State: OSPF, IS-IS
└── EGP (AS 간 / 인터넷)
    └── Path Vector: BGP
```

## 동작 방식별 비교

| 방식 | 프로토콜 | 정보 교환 방식 | 토폴로지 파악 |
|------|---------|-------------|-------------|
| **Distance Vector** | RIP, EIGRP | 라우팅 테이블 공유 | 인접 라우터까지만 |
| **Link State** | OSPF, IS-IS | LSA 전체 플러딩 | 전체 토폴로지 |
| **Path Vector** | BGP | AS 경로 정보 교환 | AS 수준 경로 |

## 주요 프로토콜 AD 비교

| 프로토콜 | 분류 | AD |
|---------|------|-----|
| EIGRP | IGP (Distance Vector) | 90 |
| OSPF | IGP (Link State) | 110 |
| RIP | IGP (Distance Vector) | 120 |
| eBGP | EGP (Path Vector) | 20 |
| iBGP | EGP (Path Vector) | 200 |

# 핵심 포인트
- 라우팅 프로토콜은 **IGP(내부)** 와 **EGP(외부/AS 간)** 로 구분
- 동작 방식에 따라 Distance Vector / Link State / Path Vector로 분류
- 각 프로토콜은 고유한 Metric과 AD 값을 가짐

# 하위 개념
- [[IGP]]
- [[EGP]]

# 관련 개념
- [[Dynamic Routing]]
- [[Best Path (Dynamic Routing)]]
- [[Administrative Distance & Metric]]
