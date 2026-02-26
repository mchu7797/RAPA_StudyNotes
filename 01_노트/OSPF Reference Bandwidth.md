---
uid: 202602231639
aliases: [Reference Bandwidth, 참조 대역폭]
tags: [network, routing, ospf, metric]
source: RAPA 수업 (2/23)
created: 2026-02-23
status: complete
---
# 개념
- OSPF는 Cost를 기준으로 경로를 선출하며, 이 값은 인터페이스의 대역폭에 반비례함.
```
cost = reference_bandwidth / interface_bandwith
```

# 핵심 포인트
- 기본 설정에서는 FastEthernet 이상의 링크를 모두 동일한 Cost로 계산하는 오류가 발생함.
- 따라서 현대 네트워크 환경에서는 모든 장비의 참조 대역폭을 동일하게 높여줘야 함.
# 나만의 언어로

# 상위 개념
- [[OSPF]]
- [[OSPF Metric]]
