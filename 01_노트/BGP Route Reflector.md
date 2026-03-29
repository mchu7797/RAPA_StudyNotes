---
uid: 202603180247
aliases: [BGP RR, Route Reflector]
tags: [network, routing, bgp, egp]
source: RAPA 수업 (3/6) - 네트워크 이론 10
created: 2026-03-18
status: complete
---
# 개념
BGP Route Reflector(RR)는 **iBGP full-mesh의 확장성 문제**를 해결하기 위한 기법이다. iBGP Split-Horizon 규칙을 완화하여, RR이 iBGP로 학습한 경로를 다른 iBGP Peer에게 재전달(Reflect)할 수 있게 한다.

## 왜 필요한가

### iBGP Full-Mesh 문제
iBGP는 **Split-Horizon** 규칙 때문에 iBGP로 받은 경로를 다른 iBGP Peer에게 전달하지 않는다. 따라서 AS 내 모든 라우터가 서로 직접 iBGP 세션을 맺어야 한다.

- 필요한 세션 수: **n(n-1)/2**
- 10대 → 45개 세션 / 100대 → 4,950개 세션 → 관리 불가능

### Route Reflector 해결 방식
RR을 지정하면 **클라이언트들이 RR에게만 세션을 맺으면** 된다. RR이 경로를 대신 전달해준다.

## 구성 요소

| 역할 | 설명 |
|------|------|
| **Route Reflector (RR)** | 경로를 반사(Reflect)하는 중앙 라우터 |
| **RR Client** | RR에게 경로를 전달받는 클라이언트 라우터 |
| **Non-Client** | RR Client가 아닌 일반 iBGP Peer |
| **Cluster** | RR + 해당 RR의 클라이언트 집합 |

## 경로 전달 규칙

| 수신 경로 출처 | 전달 대상 |
|-------------|----------|
| eBGP Peer | 모든 iBGP Peer (Client + Non-Client) |
| RR Client | 모든 iBGP Peer (Client + Non-Client) |
| Non-Client iBGP | Client에게만 전달 |

## 루프 방지 속성
RR은 경로를 반사할 때 두 가지 속성을 추가한다.

- **ORIGINATOR_ID**: 경로를 최초 광고한 라우터의 Router ID. 자신이 광고한 경로가 돌아오면 무시.
- **CLUSTER_LIST**: 경로가 거쳐온 Cluster ID 목록. 중복 Cluster ID가 있으면 루프로 판단하여 무시.

## 설정

### RR에서 클라이언트 지정
```bash
router bgp [AS 번호]
 neighbor [Client IP] remote-as [같은 AS]
 neighbor [Client IP] update-source loopback 0
 neighbor [Client IP] route-reflector-client
```

### 설정 예시 (AS 100, RR = R2)
```bash
! R2 (Route Reflector)
router bgp 100
 neighbor 1.1.1.1 remote-as 100
 neighbor 1.1.1.1 update-source loopback 0
 neighbor 1.1.1.1 route-reflector-client

 neighbor 3.3.3.3 remote-as 100
 neighbor 3.3.3.3 update-source loopback 0
 neighbor 3.3.3.3 route-reflector-client
```
- R1, R3는 클라이언트이므로 서로 직접 세션 불필요
- RR 자신은 `route-reflector-client` 명령어 불필요

## RR vs Confederation 비교

| | Route Reflector | Confederation |
|-|----------------|--------------|
| 방식 | 중앙 RR이 경로 반사 | AS를 서브 AS로 분할 |
| 설정 복잡도 | 낮음 | 높음 |
| AS 구조 변경 | 없음 | 있음 (서브 AS 도입) |
| 적합한 환경 | 대부분의 환경 | 대규모 ISP |

# 핵심 포인트
- iBGP full-mesh 문제(n*(n-1)/2 세션)를 RR로 해결
- RR Client는 RR에게만 세션을 맺으면 되므로 세션 수 대폭 감소
- 루프 방지는 **ORIGINATOR_ID**와 **CLUSTER_LIST** 속성으로 처리

# 상위 개념
- [[BGP]]
- [[BGP eBGP & iBGP]]

# 관련 개념
- [[BGP Confederation]]
- [[BGP Next-Hop-Self]]
- [[BGP Neighbor 상태]]
