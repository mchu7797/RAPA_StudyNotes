---
uid: 202602230006
aliases: [Exterior Gateway Protocol]
tags: [network, routing, routing-protocol, egp]
source: RAPA 수업 (2/23)
created: 2026-02-23
status: complete
---
# 개념
EGP(Exterior Gateway Protocol)는 **서로 다른 AS(Autonomous System) 간**에 라우팅 정보를 교환하기 위한 프로토콜이다. 현재 사실상 **BGP(Border Gateway Protocol)** 가 유일한 EGP로 사용된다.

## AS (Autonomous System)
- 단일 관리 정책 하에 운영되는 라우터 집합
- 고유한 **AS 번호(ASN)** 로 식별 (예: KT, SK, AWS 등 각각 별도 ASN 보유)
- IGP는 AS 내부, EGP는 AS 경계(Border Router)에서 동작

## IGP와의 비교

| 항목 | IGP | EGP (BGP) |
|------|-----|-----------|
| 적용 범위 | 단일 AS 내부 | AS 간 |
| 경로 선출 기준 | Metric (비용) | 정책 기반 (Path Vector) |
| 컨버전스 속도 | 빠름 | 느림 |
| 라우팅 정보량 | 상대적으로 적음 | 인터넷 전체 수준 |
| 대표 프로토콜 | OSPF, EIGRP, RIP | BGP |

## EGP가 필요한 경우
- ISP와 고객사 간 연결
- 멀티호밍(여러 ISP에 동시 연결)
- 조직 규모가 커져 여러 AS를 직접 운용하는 경우 → 내부 AS 간도 BGP 사용

# 핵심 포인트
- EGP = 사실상 **BGP만 존재** (구형 EGP 프로토콜은 사용 안 함)
- IGP에 비해 컨버전스가 느리지만, **인터넷 규모의 방대한 경로 정보** 처리 가능
- AS 간 **정책 기반 라우팅** 구현이 핵심 (단순한 최단 경로가 아님)

# 관련 개념
- [[BGP]]
- [[IGP]]
- [[Dynamic Routing Protocol]]
- [[Dynamic Routing]]
