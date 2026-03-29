---
uid: 202601210900
aliases: [LAN Switching, Collision Domain, Broadcast Domain, CSMA/CD, Hub vs Switch, MAC 학습]
tags: [switch, lan, layer2, collision, broadcast, mac]
source: 260121_네트워크_이론_5.pdf
created: 2026-01-21
status: complete
---
# 개념
스위치가 MAC 주소를 학습하여 이더넷 프레임을 올바른 포트로 전달하는 방식. 허브 환경의 충돌 문제를 해결하고 효율적인 LAN 통신을 구현한다.

# 핵심 포인트
- **Hub**: 전기 신호를 모든 포트에 복제 → Collision Domain 공유 → CSMA/CD 필요 (Half-Duplex)
- **CSMA/CD**
  - CS (Carrier Sense): 케이블에서 다른 장비가 전송 중인지 청취
  - MA (Multiple Access): 네트워크가 비어있으면 누구나 전송 가능
  - CD (Collision Detection): 충돌 감지 후 재전송
- **Switch vs Hub**
  - 스위치: 각 포트가 별도의 Collision Domain → **Full-Duplex** → 충돌 없음
  - 지능형 장치로 MAC 주소 테이블 기반 포워딩
- **MAC 주소 학습 (Flood & Learn)**
  1. 프레임 수신 시 **Src MAC**을 MAC 테이블에 학습 (포트와 매핑)
  2. Dest MAC이 테이블에 없으면 → 수신 포트 제외 **전체 Flood**
  3. 응답 수신 시 Src MAC 학습 → 이후 유니캐스트로 정확히 전달
- **Collision Domain**: 충돌이 발생할 수 있는 영역 (스위치 = 포트마다 별도 Domain)
- **Broadcast Domain**: Broadcast를 수신하는 장비들의 집합
  - 스위치는 Broadcast를 모든 포트에 전달
  - 분리 방법: 라우터 또는 VLAN

허브는 확성기(모두에게 전달), 스위치는 우체부(목적지에만 전달). 스위치는 MAC 테이블로 "누가 어느 포트에 있는지" 기억해서 정확히 배달한다.

# 상위 개념
- [[네트워크 기초]]

# 관련 개념
- [[MAC 주소]]
- [[VLAN]]
- [[802.1Q Trunk]]
- [[스위치 기본 설정]]
