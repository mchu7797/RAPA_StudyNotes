---
uid: 202602230013
aliases: [DR, BDR, Designated Router]
tags: [network, routing, ospf]
source: RAPA 수업 (2/23)
created: 2026-02-23
updated: 2026-02-25
status: complete
---
# 개념
- Broadcast (Multi-Access) 환경에서 라우터가 많은 경우 각 라우터가 LS 정보를 다른 모든 라우터에 Flooding하는 것은 비효율적이다.
- 따라서 모든 라우터가 자신의 LS 정보를 DR 라우터에 보내고 DR 라우터가 다른 라우터에게 LS 정보를 전달하는 구조를 가진다.
![[ospf_dr_bdr.png]]
# 역할 구분
- **DR** : 모든 DROTHER와 Neighbor 관계를 형성하며, LSA를 수집·배포하는 대표 라우터
- **BDR** : DR의 백업. 모든 DROTHER와 Neighbor 관계를 형성
- **DROTHER** : DR/BDR이 아닌 라우터. DROTHER 간에는 2WAY 상태만 유지 (Hello 메시지만 교환)
# 멀티캐스트 주소
- DROTHER → DR/BDR : `224.0.0.6` (LSU 전송)
- DR → DROTHER : `224.0.0.5` (LSU 전송)
# DR 선출 조건
1. **OSPF Priority**가 높은 장비가 DR로 선출됨 (기본값: 1)
2. Priority가 동일하면 **높은 Router ID**를 가진 장비가 DR로 선출됨
- Priority를 0으로 설정하면 DR/BDR 선출에 참여하지 않음 (운영 중 적용 가능)
	- DR → DROTHER로 강등
	- BDR → DR로 승격
	- DROTHER 중 BDR 재선출
- 운영 중 DR을 변경하려면 Priority 수정 후 OSPF Process 재시작 필요
	- `clear ip ospf process`
# DR/BDR 비선점 원칙
- 선출된 DR/BDR은 이후 더 높은 우선순위의 장비가 추가되거나, 우선순위가 변경되더라도 재선출되지 않음
# DR/BDR 재선출 조건
1. **DR 장애** : BDR → DR 승격, DROTHER 중 BDR 재선출
2. **DR의 Priority를 0으로 변경** : DR → DROTHER, BDR → DR 승격, DROTHER 중 BDR 재선출
3. **모든 장비 OSPF 재설정** : DR/BDR 전체 재선출
# 상위 개념
- [[OSPF]]