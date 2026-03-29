---
uid: 202603040846
aliases: [BGP Advertisement, BGP 경로 광고 방식]
tags: [network, routing, bgp]
source: RAPA 수업 (3/3) - 네트워크 이론 9
created: 2026-03-04
status: draft
---
# 개념
BGP는 이웃 라우터에게 경로를 광고하는 방식에 따라 3가지로 분류한다.

## Default Route Advertisement
- 이웃 라우터에게 **기본 경로(0.0.0.0/0)만** 광고하는 방식
- 고객 네트워크(소규모 ISP, 기업)에 인터넷 연결을 제공할 때 사용
- 설정 : `neighbor x.x.x.x default-originate`
- 조건 : 라우팅 테이블에 0.0.0.0/0 경로가 없어도 광고 가능 (강제 광고)

## Partial Routing Updates (부분 라우팅 업데이트)
- 전체 인터넷 라우팅 테이블 대신 **일부 경로(특정 prefix)만** 광고
- 예: 고객 경로, 특정 지역 경로만 전달
- 기본 경로와 함께 사용하는 경우가 많음 (Default + 특정 경로)
- 수신 라우터의 메모리/CPU 부담이 적음

## Full Routing Updates (전체 라우팅 업데이트)
- 인터넷의 **모든 경로(Full Internet Routing Table)** 를 광고
- 현재 인터넷 라우팅 테이블은 약 900,000개 이상의 prefix
- ISP 간 피어링에서 주로 사용
- 수신 라우터는 충분한 메모리와 처리 능력이 필요

# 핵심 포인트
- **Default Route** : 작은 경로 테이블로 운영 가능, but 최적 경로 선택 불가
- **Full Routing Table** : 최적 경로 선택 가능, but 높은 리소스 필요
- 실제 환경에서는 네트워크 규모와 역할에 따라 적절한 방식을 선택한다.


# 상위 개념
- [[BGP]]

# 관련 개념
- [[BGP Network Advertise]]
- [[BGP 테이블]]
