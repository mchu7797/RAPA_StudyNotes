---
uid: 202601120909
aliases: [기본 게이트웨이, Gateway, Default Gateway]
tags: [gateway, routing, fundamental]
source: 260112_네트워크_이론.pdf
created: 2026-01-12
status: complete
---
# 개념
호스트가 자신의 네트워크 외부에 있는 대상과 통신하기 위해 사용하는 라우터(또는 L3 스위치)의 IP 주소.

# 핵심 포인트
- 호스트는 서브넷 마스크로 목적지가 같은 네트워크인지 다른 네트워크인지 판단
  - **같은 네트워크**: ARP로 대상 MAC 직접 요청 → 직접 통신
  - **다른 네트워크**: Default Gateway의 MAC 주소를 ARP로 확인 → Gateway에게 프레임 전달
- **핵심 원칙**: L2 주소(MAC)는 홉마다 변경되지만, L3 주소(IP)는 출발지~목적지까지 불변
- 스위치 관리를 위한 Default Gateway 설정: `ip default-gateway [IP 주소]`
- 라우터 또는 L3 스위치를 Default Gateway로 사용

동네 밖으로 나가려면 반드시 지나야 하는 "마을 입구 대문". 외부로 나가는 모든 패킷은 게이트웨이(라우터)를 거친다.

# 상위 개념
- [[네트워크 기초]]

# 관련 개념
- [[ARP]]
- [[IP 라우팅]]
- [[IPv4 주소 & 클래스]]
