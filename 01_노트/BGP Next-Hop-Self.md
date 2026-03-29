---
uid: 202603040850
aliases: [next-hop-self, BGP Next Hop 문제]
tags: [network, routing, bgp, ibgp]
source: RAPA 수업 (3/3) - 네트워크 이론 9
created: 2026-03-04
status: draft
---
# 개념
iBGP 환경에서 발생하는 **Next-Hop 문제**와 그 해결책이다.

## 문제 발생 원인
- eBGP Neighbor로부터 경로를 수신한 Edge 라우터가 iBGP Neighbor에게 그 경로를 광고할 때,
  **Next-Hop 주소를 변경하지 않고 그대로 전달**한다.
- 즉, Next-Hop = eBGP Neighbor의 IP (AS 외부 IP)
- iBGP 라우터들은 그 외부 IP에 대한 경로를 IGP 테이블에서 찾을 수 없음
  → Next-Hop Unreachable → BGP 테이블에서 `*`(Valid)가 붙지 않음 → 경로 사용 불가

```
[외부 AS] ─── R1(Edge) ─── R2(내부 iBGP)
         eBGP         iBGP

R1이 R2에게 1.0.0.0/24 광고 시 Next-Hop = 외부 IP (예: 172.16.12.1)
R2는 172.16.12.1을 모름 → 경로 무효
```

## 해결 방법 : next-hop-self
```
R1(config-router)# neighbor R2의IP next-hop-self
```
- Edge 라우터(R1)가 iBGP Neighbor(R2)에게 경로를 광고할 때 **Next-Hop을 자신의 IP로 변경**
- R2는 R1의 IP를 IGP(OSPF 등)를 통해 이미 알고 있음 → Next-Hop Reachable → 경로 유효

```
설정 후:
R1이 R2에게 1.0.0.0/24 광고 시 Next-Hop = R1의 IP (예: 10.1.12.1)
R2는 10.1.12.1을 OSPF로 알고 있음 → 경로 유효 ✓
```

## 확인 명령어
```
show ip bgp
! Next Hop 컬럼에서 자신의 IP가 표시되는지 확인

show ip bgp neighbors x.x.x.x advertised-routes
! 실제 광고하는 경로와 Next-Hop 확인
```

# 핵심 포인트
- **Next-Hop-Self는 iBGP 환경에서 거의 필수 설정**이다.
- Edge 라우터에서 **모든 iBGP Neighbor에 대해** next-hop-self를 설정해야 한다.
- 이 설정은 경로를 받는 쪽(R2)이 아니라 **경로를 광고하는 쪽(R1, Edge 라우터)에 설정**한다.

이때 대전역(Edge 라우터, R1)이 "일단 나(대전역)한테 와. 거기서 내가 연결해줄게"라고 티켓의 환승역을 **자기 자신(대전역)으로 바꿔서** 전달하는 것이 next-hop-self다.
서울역 입장에서는 대전역이 어딘지 KTX 노선(IGP)으로 이미 알고 있으므로 문제없이 출발할 수 있다.

# 상위 개념
- [[BGP eBGP & iBGP]]
- [[BGP]]

# 관련 개념
- [[BGP 테이블]]
- [[BGP Split-Horizon]]