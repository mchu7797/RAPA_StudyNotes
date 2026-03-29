---
uid: 202602230010
aliases: [Dijkstra, 다익스트라]
tags: [network, routing, ospf, algorithm]
source: RAPA 수업 (2/23)
created: 2026-02-23
status: complete
---
# 개념
SPF(Shortest Path First) 알고리즘은 OSPF에서 사용하는 최단 경로 탐색 알고리즘으로, **다익스트라(Dijkstra) 알고리즘**과 동일하다. 각 라우터는 수집한 LSDB(Link-State Database)를 토대로 자신을 루트(Root)로 하는 **최단 경로 트리**를 계산한다.

## 동작 과정
1. **LSDB 수집**: 네트워크 내 모든 라우터의 LSA를 플러딩으로 수집
2. **SPF 트리 계산**: 자신을 루트로 각 목적지까지의 최단 경로 계산
   - 미방문 노드 중 **Cost가 가장 낮은 노드**를 순서대로 방문
   - 방문할 때마다 인접 노드의 누적 Cost 갱신
3. **라우팅 테이블 등록**: 계산된 최단 경로를 라우팅 테이블에 반영

## Cost 계산
OSPF의 Metric인 **Cost = 10^8 / 링크 대역폭(bps)**

| 링크 속도 | Cost |
|---------|------|
| 100 Mbps | **1** |
| 10 Mbps | **10** |
| 1.544 Mbps (T1) | **64** |

- Cost가 낮을수록 선호 → 빠른 링크를 자동으로 선택

## SPF 재계산 트리거
- 새로운 라우터/링크 추가
- 링크 다운/업
- LSA 업데이트 수신 시

→ 재계산은 CPU 부하를 유발하므로, 빈번한 토폴로지 변화는 성능에 영향

# 핵심 포인트
- SPF = 다익스트라 알고리즘 → LSDB 기반으로 최단 경로 트리 계산
- 모든 OSPF 라우터가 **동일한 LSDB**를 가지므로 동일한 SPF 결과 도출
- 토폴로지 변화 시 SPF 재계산 → 컨버전스 발생

# 상위 개념
- [[OSPF]]

# 관련 개념
- [[Link-State Database (LSDB)]]
- [[Link-State Advertisements (LSA)]]
- [[OSPF Metric]]
