---
uid: 202601120906
aliases: [MAC Address, Physical Address, 이더넷 주소, 하드웨어 주소]
tags: [mac, layer2, ethernet]
source: 260112_네트워크_이론.pdf
created: 2026-01-12
status: complete
---
# 개념
OSI Layer 2(데이터 링크)에서 사용하는 물리적 주소. NIC에 하드웨어적으로 고정된 고유 주소로, 같은 네트워크(LAN) 안에서 장비를 식별한다.

# 핵심 포인트
- 48bit, 16진수 표기 (예: AA:BB:CC:DD:EE:FF)
  - 앞 24bit (OUI): LAN카드 **제조업체** 식별
  - 뒤 24bit: 제품 **일련번호**
- NIC에 하드웨어적으로 고정 → **변경 불가능** (논리적 주소인 IP와 다름)
- **이더넷 프레임 헤더 구조**: Dest MAC (48bit) + Src MAC (48bit) + Ether Type (16bit) + ... + FCS (4byte)
- 스위치는 MAC 주소를 기반으로 프레임 전달 (MAC 주소 테이블 사용)
- **특수 MAC 주소**: FF:FF:FF:FF:FF:FF = Broadcast (모든 장비 수신)
- LAN 통신 = L2 (MAC 주소 사용) / WAN 통신 = L3 (IP 주소 사용)

같은 동네(LAN) 안에서 집을 찾는 "집 호수" 같은 주소. IP가 우편번호(논리적, 변경 가능)라면 MAC은 집 호수(물리적, 고정)다.

# 상위 개념
- [[TCP-IP 모델]]
- OSI Layer 2

# 관련 개념
- [[ARP]]
- [[LAN Switching]]
- [[프로토콜 & 캡슐화]]
