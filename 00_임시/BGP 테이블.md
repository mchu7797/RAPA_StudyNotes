---
uid: 202603040848
aliases: [BGP RIB, BGP Routing Table, show ip bgp]
tags: [network, routing, bgp]
source: RAPA 수업 (3/3) - 네트워크 이론 9
created: 2026-03-04
status: draft
---
# 개념
BGP는 수신한 모든 경로를 **BGP 테이블(RIB, Routing Information Base)** 에 저장한다.
BGP 테이블의 최적 경로만 라우팅 테이블(RIB)에 설치된다.

## show ip bgp 출력 해석
```
BGP table version is 5, local router ID is 1.1.1.1
   Network          Next Hop         Metric LocPrf Weight Path
*> 1.1.1.0/24       0.0.0.0               0         32768 i
*  10.0.0.0/8       192.168.12.2          0             0 2 i
*> 10.0.0.0/8       192.168.13.3          0             0 3 i
```

| 코드 | 의미 |
|------|------|
| `*` | Valid Route (Next-Hop 도달 가능, 유효한 경로) |
| `>` | Best Path (최적 경로, 라우팅 테이블에 설치됨) |
| `i` | iBGP로 학습한 경로 |
| (없음) | Invalid (Next-Hop 도달 불가) |

## BGP Best Path 선택 기준 (우선순위 순)
1. **Weight** : Cisco 독자 속성, 높을수록 선호, 로컬 라우터에만 적용
2. **Local Preference** : iBGP 내에서 출구 경로 선택, 높을수록 선호 (기본 100)
3. **Originated** : locally originated 경로 선호 (network/redistribute > iBGP)
4. **AS Path Length** : 짧을수록 선호
5. **Origin Code** : IGP(i) > EGP(e) > Incomplete(?)
6. **MED** : 동일 AS로부터의 경로 중 낮을수록 선호
7. **eBGP > iBGP** : eBGP로 학습한 경로 선호
8. **IGP Metric** : Next-Hop까지의 IGP 메트릭이 낮을수록 선호
9. **Oldest Path** : 가장 오래된 eBGP 경로 선호
10. **Router ID** : BGP Router ID가 낮을수록 선호
11. **Neighbor IP** : Neighbor IP가 낮을수록 선호

# 핵심 포인트
- BGP 테이블에서 `*>`이 붙은 경로가 라우팅 테이블에 등록되는 최적 경로이다.
- Next-Hop이 도달 불가능하면 `*`(valid)도 붙지 않아 경로로 사용될 수 없다.
- iBGP로 학습한 경로를 최적 경로로 쓰려면 **Next-Hop이 IGP로 도달 가능해야 한다.**

# 나만의 언어로
<!-- 이 개념을 누군가에게 설명한다면? 비유, 요약, 한 줄 정리 등 -->

# 상위 개념
- [[BGP]]

# 관련 개념
- [[BGP Path Vector]]
- [[BGP Next-Hop-Self]]
- [[BGP Network Advertise]]
