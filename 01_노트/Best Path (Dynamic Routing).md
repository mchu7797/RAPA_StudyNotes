# 개념
- 라우터가 학습한 경로 중 **가장 좋은** 경로
	- 가장 좋은 경로란, **해당 목적지로 가기 위한 가장 빠른** 경로를 말함.
	- [[Dynamic Routing Protocol]]의 경로 탐색 알고리즘을 사용하여 해를 구함.
- 라우팅 테이블에 등록
## 경로 선출 우선순위
1. Administrative Distance
2. Metric ([[Dynamic Routing Protocol]]마다 계산법이 다름. AD가 동일한 경우ㄴㅇ 라ㅓ)
	- RIP - Hop Count
	- OSPF - Cost
	- ISIS - Cost
	- EIGRP - Metric
## 경로 선택
- Longest Match
# 관련 개념
- [[Dynamic Routing]]
- [[Dynamic Routing Protocol]]