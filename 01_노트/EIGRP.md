---
uid: 202602230007
aliases: [Enhanced Interior Gateway Routing Protocol]
tags: [network, routing, routing-protocol, igp, eigrp]
source: RAPA 수업 (2/23)
created: 2026-02-23
status: complete
---
# 개념
- 경로의 거리(Distance)와 방향(Vector, Next-Hop) 정보를 인접 라우터에게 수집 및 광고
- 먼저 자신의 Routing Table 생성 후 라우팅 테이블을 인접 라우터에게 전달
	- 라우터와 라우터 간의 최적 경로만 교환함
- 라우터는 직접 연결된 인접 라우터와 그 인접 라우터가 광고한 네트워크 목록만 학습
	- 즉, 직접 연결된 인접 라우터 이상의 상세한 토폴로지 정보를 가지고 있지 않음.
# 핵심 포인트
- EIGRP는 거리 벡터 기반 라우팅 프로토콜에 속한다.
- 여기서 핵심은, 라우터는 다른 라우터에게 정보를 보낼 때 모든 가공이 끝난 최종 형태의 라우팅 테이블을 넘긴다는 점이고, 다른 라우터는 그 정보를 그대로 수용한다. 다른 접근 방법은 모른다.
# 참고
- EIGRP는 원래 Cisco 독점이었다가, 2016년 5월에 RFC7868이라는 기술 문서를 통해 표준화되었다.
# 나만의 언어로

# 관련 개념
- [[IGP]]
- [[Dynamic Routing]]
- [[Dynamic Routing Protocol]]
- [[OSPF]]
- [[Administrative Distance]]
- [[Redistribute]]