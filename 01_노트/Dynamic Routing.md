---
uid: 202602230002
aliases: [동적 라우팅]
tags: [network, routing, dynamic-routing]
source: RAPA 수업 (2/23)
created: 2026-02-23
status: complete
---
# 개념
Dynamic Routing Protocol을 사용해 라우터 간 경로 정보를 자동으로 교환하고, 학습된 경로 중 최적 경로를 라우팅 테이블에 등록하여 통신하는 방식이다.

네트워크 변화(링크 장애, 새 네트워크 추가)가 발생하면 라우터들이 자동으로 경로를 재계산한다 → **컨버전스(Convergence)**.

## Static Routing과 비교

| | Dynamic Routing | Static Routing |
|-|----------------|---------------|
| 경로 갱신 | 자동 | 수동 |
| 장애 대응 | 자동 재계산 | 수동 수정 |
| 설정 복잡도 | 높음 | 낮음 |
| 리소스 사용 | CPU/메모리 사용 | 거의 없음 |
| 확장성 | 높음 | 낮음 |

## 동작 방식
1. 라우터가 인접 라우터와 **Neighbor 관계** 형성
2. 라우팅 정보 교환 (프로토콜마다 방식 다름)
3. 수신한 정보를 바탕으로 **최적 경로(Best Path) 선출**
4. 라우팅 테이블에 등록 → 패킷 포워딩에 사용

## 컨버전스 (Convergence)
네트워크 변화가 발생했을 때, 모든 라우터의 라우팅 테이블이 동일하게 수렴되는 것. 컨버전스 시간이 짧을수록 빠르게 복구된다.
- **Distance Vector** (EIGRP, RIP): 인접 라우터에게만 정보 전달 → 느린 편
- **Link State** (OSPF, IS-IS): 전체 토폴로지 공유 → 빠른 편

# 핵심 포인트
- 라우팅 테이블을 관리자가 아닌 **라우터 스스로 유지**
- 대규모 네트워크에서 필수 → 수동 관리가 불가능한 환경
- 프로토콜에 따라 Best Path 선출 기준(Metric)이 다름

# 하위 개념
- [[IGP]]
- [[EGP]]

# 관련 개념
- [[Static Routing]]
- [[Dynamic Routing Protocol]]
- [[Best Path (Dynamic Routing)]]
- [[Administrative Distance]]
- [[Redistribute]]
