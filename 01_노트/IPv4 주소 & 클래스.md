---
uid: 202601140900
aliases: [IPv4, IP Address, IP 클래스, 서브넷, 서브넷팅, 서브넷 마스크, NAT, 사설IP, 공인IP]
tags: [ip, ipv4, addressing, fundamental, subnetting]
source: 260114_네트워크_이론_2.pdf
created: 2026-01-14
status: complete
---
# 개념
IPv4는 32비트로 구성된 인터넷 계층 주소. Network Part + Host Part로 구성되며 같은 Network Part면 라우터 없이 통신 가능하다.

# 핵심 포인트
- 32bit → 8bit(1옥텟) 씩 4그룹, 10진수 점 표기법 (0.0.0.0 ~ 255.255.255.255), 총 약 43억 개
- **Network Part**: 다른 네트워크와 구분 / **Host Part**: 같은 네트워크 내 호스트 구분
- **IP 클래스**
  - A클래스: 0~126.x.x.x, Network 8bit + Host 24bit (1677만 Host/Network)
  - B클래스: 128~191.x.x.x, Network 16bit + Host 16bit (65534 Host/Network)
  - C클래스: 192~223.x.x.x, Network 24bit + Host 8bit (254 Host/Network)
  - D클래스: 224~239.x.x.x → 멀티캐스트 용도
  - 127.x.x.x → Loopback 대역
- **특수 주소**: Host Part 모두 0 = **네트워크 주소**, 모두 1 = **브로드캐스트 주소** (호스트 사용 불가)
- **서브넷팅(Subnetting)**: 대규모 네트워크를 작은 서브넷으로 분할 (Network Part 확장)
- **서브넷 마스크**: Network/Host Part 경계 식별용 32bit 값, 연속된 1과 연속된 0으로 구성
- **공인 IP (Public IP)**: 인터넷에서 유일하게 사용하는 주소
- **사설 IP (Private IP)**: 조직 내부에서 자유롭게 사용
  - A: 10.0.0.0/8 / B: 172.16.0.0~172.31.x.x/12 / C: 192.168.0.0/16
- **NAT (Network Address Translation)**: 사설 IP ↔ 공인 IP 주소 변환 기술 (라우터·공유기에 구현)

IP 주소는 인터넷의 집 주소. Network Part는 동네 이름, Host Part는 집 번호. 서브넷팅은 큰 동네를 작은 블록으로 나누는 것. NAT는 사내 내선번호를 외부 공개번호로 바꿔주는 교환원.

# 상위 개념
- [[TCP-IP 모델]]

# 관련 개념
- [[ARP]]
- [[Default Gateway]]
- [[IP 라우팅]]
