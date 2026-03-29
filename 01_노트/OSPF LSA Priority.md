---
uid: 202602250903
aliases: [LSA 우선순위, OSPF 경로 우선순위]
tags: [network, routing, ospf, lsa]
source: RAPA 수업 (2/25)
created: 2026-02-25
status: complete
---
# 개념
- OSPF는 동일 목적지에 대해 여러 LSA Type으로 경로를 학습할 수 있음
- 이 경우 LSA Type에 따른 우선순위로 최적 경로를 결정함
# 경로 우선순위
```
O (Intra-Area)  >  O IA (Inter-Area)  >  O E1 (External Type-1)  >  O E2 (External Type-2)
```
| 순위 | 코드 | 설명 | LSA Type |
|---|---|---|---|
| 1 | `O` | 같은 Area 내부 경로 (가장 신뢰) | Type-1 |
| 2 | `O IA` | 다른 Area의 경로 (ABR 경유) | Type-3 |
| 3 | `O E1` | 외부 경로 (변동 Cost, Hop마다 Cost 증가) | Type-5 |
| 4 | `O E2` | 외부 경로 (고정 Cost, Hop 무관) | Type-5 |
# 핵심 포인트
- OSPF는 같은 Area의 경로(`O`)를 가장 신뢰함
- `O` 경로가 없으면 다른 Area의 경로(`O IA`)를 선택함
- `O IA`도 없으면 Cost가 변동하는 외부 경로(`O E1`)를 선택함
- 최후에 고정 Cost 외부 경로(`O E2`)를 선택함
- Cost 값이 아무리 높아도 상위 우선순위의 경로가 항상 선택됨
	- 예: `O` Cost 1001 > `O IA` Cost 11
# 검증 예시
1. `O` 경로 존재 시: `O 1.1.1.1 [110/1001]` 선택
2. `O` 경로 제거 후: `O IA 1.1.1.1 [110/11]` 선택
3. `O IA` 경로 제거 후: `O E1 1.1.1.1 [110/30]` 선택 (Hop에 따라 Cost 변동)
4. `O E1` 경로 제거 후: `O E2 1.1.1.1 [110/20]` 선택 (Hop과 무관하게 Cost 고정)
# 상위 개념
- [[OSPF]]
# 관련 개념
- [[OSPF LSA Type]]
- [[Redistribute]]
- [[OSPF Metric]]
