---
uid: 202601280901
aliases: [Administrative Distance, AD, Metric, Best Path, 최적 경로 선출, Distance Vector, Link State]
tags: [routing, ad, metric, best-path, dynamic-routing]
source: 260128_네트워크_이론_6.pdf
created: 2026-01-28
status: complete
---
# 개념
라우터가 여러 소스에서 학습한 경로들 중 최적 경로를 선출하는 기준. AD → Metric → Longest Match 순서로 경로를 결정한다.

# 핵심 포인트

### Best Path 선출 순서
1. **Administrative Distance (AD)**: 서로 다른 라우팅 프로토콜 간 신뢰도 비교 → **낮을수록 신뢰도 높음**
2. **Metric**: 동일한 프로토콜 내 최적 경로 비교 → **낮을수록 좋은 경로**
3. **Longest Match**: 가장 구체적인(긴) 경로 선택

---

### Administrative Distance (AD)
- 하나의 목적지에 두 개 이상의 프로토콜이 경로를 제공할 때, 어느 프로토콜의 경로를 신뢰할지 결정
- 로컬 값 (다른 라우터에 전달되지 않음), 벤더마다 다를 수 있음

| 소스 | AD 값 |
|------|-------|
| Directly Connected | **0** |
| Static Route | **1** |
| EIGRP Summary | 5 |
| External BGP | 20 |
| EIGRP | **90** |
| OSPF | **110** |
| IS-IS | 115 |
| RIP | **120** |
| External EIGRP | 170 |
| Internal BGP | 200 |
| Unknown | 255 (사용 불가) |

---

### Metric
- 동일한 라우팅 프로토콜에서 같은 목적지로 가는 여러 경로 중 최적 경로 선출 기준
- 프로토콜마다 계산 방법이 다름:
  - **RIP**: Hop Count (거쳐가는 라우터 수)
  - **OSPF**: Cost (링크 대역폭 기반, `10^8 / Bandwidth`)
  - **IS-IS**: Cost
  - **EIGRP**: 복합 메트릭 (대역폭, 지연 등)

---

### Distance Vector vs Link State
- **Distance Vector** (RIP, EIGRP)
  - 경로의 거리(Distance)와 방향(Vector/Next-Hop)만 인접 라우터와 교환
  - 직접 연결된 라우터가 광고한 목록만 학습 → 전체 토폴로지 모름
  - 라우팅 테이블 생성 후 인접 라우터에게 테이블 전달
- **Link State** (OSPF, IS-IS)
  - 자신과 자신의 링크 상태 정보(LSA)를 네트워크 전체에 전달
  - 모든 라우터가 동일한 전체 토폴로지 정보 학습 → SPF 알고리즘으로 최적 경로 계산
  - 네트워크 규모에 비례하여 CPU/RAM 리소스 증가

# 나만의 언어로
<!-- 이 개념을 누군가에게 설명한다면? 비유, 요약, 한 줄 정리 등 -->
AD = 어느 정보 출처를 믿을지 (경찰 공문 vs 소문). Metric = 같은 출처에서 온 여러 경로 중 어느 길이 더 빠른지. AD가 먼저이고, AD 같으면 Metric으로 결정.

# 상위 개념
- [[IP 라우팅]]

# 관련 개념
- [[Dynamic Routing Protocol]]
- [[Longest Match Rule]]
- [[Static Routing]]
