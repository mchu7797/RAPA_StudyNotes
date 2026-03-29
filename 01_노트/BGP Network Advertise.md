---
uid: 202603040849
aliases: [BGP network command, BGP 경로 주입]
tags: [network, routing, bgp]
source: RAPA 수업 (3/3) - 네트워크 이론 9
created: 2026-03-04
status: draft
---
# 개념
BGP에 경로를 광고하려면 먼저 **BGP 테이블에 경로를 주입(Inject)** 해야 한다.
주입 방법은 두 가지이다.

## 1. network 명령어
```
router bgp 1
  network 10.0.0.0 mask 255.255.255.0
```
- **라우팅 테이블에 정확히 일치하는 경로가 존재해야 BGP 테이블에 등록됨**
- 존재하지 않으면 등록 안 됨 (자동 광고 X)
- 일반적으로 Static Route 또는 Connected Route를 먼저 만들어두고 network 명령 사용

## 2. redistribute 명령어
```
router bgp 1
  redistribute ospf 1
  redistribute connected
  redistribute static
```
- 다른 라우팅 프로토콜(OSPF, EIGRP 등) 또는 연결된 네트워크/정적 경로를 BGP로 재배포
- Origin Code가 `?` (Incomplete)로 설정됨
- 세밀한 제어가 필요하면 route-map과 함께 사용

## network vs redistribute 비교
| 항목 | network | redistribute |
|------|---------|--------------|
| Origin Code | `i` (IGP) | `?` (Incomplete) |
| 정밀도 | 정확한 prefix 지정 | 프로토콜 단위 |
| 라우팅 테이블 의존 | 필요 (exact match) | 해당 프로토콜의 경로 |

# 핵심 포인트
- `network` 명령어는 **자동 요약(Auto-Summary)을 조심**해야 한다. (기본적으로 classful 네트워크로 요약될 수 있음)
- `no auto-summary` 명령어로 자동 요약 비활성화 권장
- BGP는 경로를 광고받았다고 즉시 사용하는 게 아니라, 유효성(Valid)을 확인 후 최적 경로를 선택한다.


# 상위 개념
- [[BGP]]

# 관련 개념
- [[BGP 테이블]]
- [[BGP Advertisements]]
- [[Redistribute]]
