---
uid: 202603040847
aliases: [Path Vector, BGP 경로 벡터]
tags: [network, routing, bgp]
source: RAPA 수업 (3/3) - 네트워크 이론 9
created: 2026-03-04
status: draft
---
# 개념
BGP는 **경로 벡터(Path Vector)** 기반 라우팅 프로토콜이다.

- 거리 벡터(Distance Vector)처럼 경로 정보를 인접 라우터에 전달하지만,
  단순 거리(홉 수, 메트릭) 대신 **AS 경로 목록(AS_PATH)**을 함께 전달한다.
- 라우터는 UPDATE 메시지에 자신의 AS 번호를 AS_PATH에 추가하여 전달한다.

## 루프 방지
- 경로 광고를 받은 라우터가 AS_PATH 목록에 **자신의 AS 번호가 포함되어 있으면 해당 경로를 폐기**
- 이를 통해 라우팅 루프를 방지함

## 예시
```
AS 1 → AS 2 → AS 3 으로 1.0.0.0/24 경로가 전달될 때:
  AS 1이 광고 : AS_PATH = [1]
  AS 2가 AS 3에 광고 : AS_PATH = [2, 1]
  AS 3이 AS 1에 광고하려 하면 : AS_PATH = [3, 2, 1] → AS 1은 자신의 AS가 있으므로 폐기
```

## 경로 선택
- AS_PATH가 짧을수록 선호 (기본적으로)
- BGP는 최적 경로를 선택할 때 다양한 **Path Attribute**를 종합적으로 고려함
- 경로 선택 우선순위: Weight → Local Preference → Originated → AS Path Length → Origin Code → MED → ...

# 핵심 포인트
- BGP의 루프 방지 = **AS_PATH를 통한 자신의 AS 번호 감지**
- 단순 최단 경로가 아닌 **정책(Policy) 기반 경로 선택**이 BGP의 핵심
- AS_PATH 조작(prepending)으로 경로 선호도를 인위적으로 조정할 수 있다.


# 상위 개념
- [[BGP]]

# 관련 개념
- [[BGP Advertisements]]
- [[BGP 테이블]]
- [[EGP]]
