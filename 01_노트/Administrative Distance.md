# 개념
- 하나의 목적지에 대해 두 개 이상의 라우팅 프로토콜이 경로를 제공하고 있을 때, 해당 경로를 라우팅 테이블에 추가하기 위한 라우팅 프로토콜 신뢰도
- 낮을수록 신뢰도가 높음.
- Local에 적용되는 값으로, 다른 장비에 전달되지 않음.
- 각 벤더마다 설정 값이 다를 수 있고, 변경도 가능함.
# 예시

| Source             | Administrative Distance |
| ------------------ | :---------------------- |
| Directly Connected | 0                       |
| Static Route       | 1                       |
| External BGP       | 20                      |
| EIGRP              | 90                      |
| OSPF               | 110                     |
| RIP                | 120                     |
| External EIGRP     | 170                     |
| Internal BGP       | 200                     |
|                    |                         |
# 관련 개념
- [[Static Routing]]
- [[Dynamic Routing]]
- [[Dynamic Routing Protocol]]
- [[EGP]]
- [[EIGRP]]
- [[OSPF]]