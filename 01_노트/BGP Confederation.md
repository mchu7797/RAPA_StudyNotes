---
uid: 202603180246
aliases: [BGP 연합 AS, BGP Confederations]
tags: [network, routing, bgp, egp]
source: RAPA 수업 (3/6) - 네트워크 이론 10
created: 2026-03-18
status: draft
---
# 개념
BGP Confederation은 하나의 큰 AS를 여러 개의 **서브 AS(Sub-AS)** 로 나눠서 운영하는 방법이다.

- 외부(진짜 eBGP 피어)에는 단일 AS처럼 보이지만,
- 내부에서는 서브 AS 간 eBGP 형태로 정책을 적용할 수 있다.
- iBGP full-mesh 확장 한계를 줄이기 위한 설계 기법이다.

## 왜 쓰는가
- 대규모 iBGP 환경에서 full-mesh 구성 부담을 줄이기 위해 사용
- AS를 논리적으로 분할해 운영/정책 관리를 단순화
- 외부 AS에는 내부 구조를 숨기고 기존 AS 정체성 유지

## 기본 동작
- `bgp confederation identifier <공용 AS>`: 외부에 보일 대표 AS
- `bgp confederation peers <서브AS 목록>`: 같은 confederation에 속한 다른 서브 AS 지정
- 서브 AS 간 경로 교환 시 BGP 테이블에 `confed-internal` 또는 `confed-external` 상태로 표시될 수 있음

## 설정 예시
```bash
router bgp 24
 bgp confederation identifier 2
 bgp confederation peers 35
 neighbor 3.3.3.3 remote-as 35
 neighbor 3.3.3.3 update-source loopback 0
 neighbor 3.3.3.3 ebgp-multihop 2
```

# 핵심 포인트
- Confederation은 "AS를 나눠서 iBGP 확장성 문제를 다루는 방법"이다.
- 외부에는 단일 AS처럼 동작하므로 대외 정책/식별 일관성을 유지한다.
- 서브 AS 간 세션은 eBGP처럼 보이지만, confederation 문맥에서 특별히 해석된다.


# 상위 개념
- [[BGP]]
- [[BGP eBGP & iBGP]]

# 관련 개념
- [[BGP Path Vector]]
- [[BGP 테이블]]
- [[BGP Neighbor 상태]]
