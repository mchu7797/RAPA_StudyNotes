---
uid: 202603040843
aliases: [External BGP, Internal BGP, eBGP, iBGP]
tags: [network, routing, bgp, egp]
source: RAPA 수업 (3/3) - 네트워크 이론 9
created: 2026-03-04
status: draft
---
# 개념
- **eBGP (External BGP)** : 서로 다른 AS 번호를 가진 라우터 간의 BGP 세션
- **iBGP (Internal BGP)** : 동일한 AS 내에서 동작하는 BGP 세션

## eBGP 특징
- 일반적으로 직접 연결된 인터페이스 IP를 사용하여 Neighbor를 맺음
- 기본 TTL 값이 1 → 직접 연결되지 않은 경우 `ebgp-multihop` 설정 필요
- eBGP Neighbor에게 경로를 광고할 때 **Next-Hop이 자신의 IP로 변경됨**
- `neighbor x.x.x.x remote-as [다른 AS번호]`

## iBGP 특징
- 직접 연결되지 않아도 됨 (Loopback 인터페이스 사용 권장)
- Loopback 사용 시 `neighbor x.x.x.x update-source loopback 0` 필요
- iBGP Neighbor에게 경로를 광고할 때 **Next-Hop이 변경되지 않음** → [[BGP Next-Hop-Self]] 문제 발생
- `neighbor x.x.x.x remote-as [같은 AS번호]`
- **iBGP Split-Horizon** : iBGP로 학습한 경로는 다른 iBGP Neighbor에게 전달하지 않음
  → [[BGP Route Reflector]]로 해결

# 핵심 포인트
- eBGP와 iBGP의 핵심 차이는 **AS 번호가 같냐 다르냐**이다.
- iBGP는 AS 내부에서 eBGP로 학습한 경로를 전달하기 위해 사용한다.
- iBGP는 full-mesh 구성이 기본 → 라우터 수가 많아지면 [[BGP Route Reflector]]로 해결

# 나만의 언어로
<!-- 이 개념을 누군가에게 설명한다면? 비유, 요약, 한 줄 정리 등 -->

# 상위 개념
- [[BGP]]

# 관련 개념
- [[BGP Next-Hop-Self]]
- [[BGP Route Reflector]]
- [[BGP Neighbor 상태]]
