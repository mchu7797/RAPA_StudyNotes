---
uid: 202601120907
aliases: [Address Resolution Protocol, ARP 테이블, ARP Request, ARP Reply]
tags: [arp, layer2, layer3, fundamental]
source: 260112_네트워크_이론.pdf
created: 2026-01-12
status: complete
---
# 개념
IPv4 주소로 MAC 주소를 알아내는 프로토콜. IP와 MAC 주소의 매핑 정보를 ARP 테이블에서 관리한다.

# 핵심 포인트
- **ARP Request**: Broadcast (FF:FF:FF:FF:FF:FF)로 "이 IP를 가진 장비의 MAC 주소를 알려주세요"
- **ARP Reply**: 해당 IP를 가진 장비가 Unicast로 "내 MAC 주소는 ○○입니다" 응답
- 목적지가 **같은 네트워크** → 대상 IP의 MAC 주소를 ARP로 직접 요청
- 목적지가 **다른 네트워크** → 기본 게이트웨이(라우터)의 MAC 주소를 ARP로 요청
- ARP 테이블에 항목이 없는 경우에만 ARP Request(Broadcast) 전송
- `arp -a` 명령으로 ARP 테이블 확인 (Windows/Linux)
- ARP 테이블 항목은 일정 시간 후 자동 삭제 (aging)

전화번호부 없이 이름(IP)만 알 때 동네 방송(Broadcast)으로 "홍길동 씨 전화번호 알려주세요!"하는 것. 홍길동이 직접 응답하면 그게 ARP Reply.

# 상위 개념
- [[TCP-IP 모델]]
- [[MAC 주소]]

# 관련 개념
- [[ICMP]]
- [[Default Gateway]]
- [[IPv4 주소 & 클래스]]
- [[IP 라우팅]]
