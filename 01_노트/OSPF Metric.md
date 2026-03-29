---
uid: 202602230014
aliases: [OSPF Cost]
tags: [network, routing, ospf, metric]
source: RAPA 수업 (2/23)
created: 2026-02-23
status: complete
---
# 개념
- OSPF에도 Metric이 있다. 그건 바로 Cost인데, `Reference Bandwidth / Interface Bandwidth`로 정해진다.
- 낮은 값이 우위이며, CISCO 장비의 기본 Bandwidth 값은 100Mbps이다.
- `FastEthernet`이상의 링크를 사용하는 환경에서는 OSPF가 Cost를 제대로 계산할 수 있도록 Reference Bandwidth를 변경할 필요가 있다. 
	- 기준의 일관성을 위해서 연동되는 모든 장비가 이 값을 바꿔주어야 한다.
# 상위 개념
- [[OSPF]]
# 하위 개념
- [[OSPF Metric을 변경하는 법]]
- [[OSPF Reference Bandwidth]]
# 관련 개념
- [[OSPF LSA Priority]]