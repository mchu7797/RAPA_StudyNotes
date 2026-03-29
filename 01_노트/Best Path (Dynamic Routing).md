---
uid: 202602230004
aliases: [Best Path, 최적 경로]
tags: [network, routing, dynamic-routing]
source: RAPA 수업 (2/23)
created: 2026-02-23
status: complete
---
# 개념
라우터가 여러 소스(프로토콜)로부터 동일 목적지에 대한 경로를 학습했을 때, **최종적으로 라우팅 테이블에 등록할 하나의 경로**를 선출하는 과정이다.

## 경로 선출 우선순위

```
1. Administrative Distance (AD) → 프로토콜 간 신뢰도 비교
2. Metric → 동일 프로토콜 내 경로 비교
3. Longest Match → 가장 구체적인 경로 선택
```

### 1단계: Administrative Distance
- 서로 다른 프로토콜이 같은 목적지를 광고할 때 사용
- **낮을수록 신뢰도 높음**
- 예: EIGRP(AD 90) vs OSPF(AD 110) → EIGRP 경로 선택

### 2단계: Metric
- 동일 프로토콜 내에서 여러 경로가 있을 때 사용
- **낮을수록 좋은 경로** (프로토콜마다 계산 방식 다름)
- OSPF → Cost, EIGRP → 복합 메트릭, RIP → Hop Count

### 3단계: Longest Match
- 목적지 IP와 가장 길게 일치하는 경로 우선
- 예: `192.168.1.0/24` vs `192.168.0.0/16` → `/24`가 더 구체적이므로 우선

## 동작 예시
```
목적지: 192.168.2.1
학습된 경로:
  - OSPF: 192.168.2.0/24 via 10.0.0.1 (Cost 100)
  - EIGRP: 192.168.2.0/24 via 10.0.0.2 (Metric 3000)
  - Static: 192.168.0.0/16 via 10.0.0.3

결과:
  Step 1: EIGRP(AD 90) < OSPF(AD 110) → EIGRP 경로 후보
  Step 3: /24 > /16 → 각 경로는 개별 엔트리로 등재
```

# 핵심 포인트
- **AD → Metric → Longest Match** 순서로 최적 경로 결정
- AD는 프로토콜 간 비교, Metric은 동일 프로토콜 내 비교
- Longest Match는 패킷 포워딩 시점에 라우팅 테이블 조회에서 적용

# 상위 개념
- [[Dynamic Routing]]

# 관련 개념
- [[Administrative Distance & Metric]]
- [[Dynamic Routing Protocol]]
- [[Longest Match Rule]]
