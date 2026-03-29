---
uid: 202601120905
aliases: [TCP/IP Model, 4계층 모델, 인터넷 표준, De facto Standard]
tags: [tcpip, model, fundamental]
source: 260112_네트워크_이론.pdf
created: 2026-01-12
status: complete
---
# 개념
데이터 전송 과정을 4계층으로 단순화한 모델. 실용성과 빠른 구현을 중시해 인터넷 사실상 표준(De facto Standard)이 되었다.

# 핵심 포인트
- **4계층 Application**: 웹, 이메일, 파일 전송 등 서비스 결정
  - HTTP, FTP, DHCP, TFTP, DNS, SMTP, SNMP, Telnet
- **3계층 Transport**: 데이터 전송 신뢰성 관리, 포트 번호로 애플리케이션 식별
  - **TCP**: 신뢰할 수 있는 전송 (재전송, 흐름 제어)
  - **UDP**: 신뢰할 수 없는 전송 (빠름, 오버헤드 낮음)
  - 포트 번호: 16bit (0~65535), 0~1023 = Well-Known 예약
- **2계층 Internet**: IP 주소 기반 라우팅
  - IP, ICMP, ARP, GARP
- **1계층 Network Interface**: 물리적 연결, MAC 주소 기반 이더넷 프레임 처리
- OSI 모델 = "이상적 설계", TCP/IP 모델 = "실용적 구현"
- 각 계층 주소
  - L2: MAC 주소 (48bit, 이더넷 헤더)
  - L3: IP 주소 (32bit, IP 헤더)
  - L4: 포트 번호 (16bit, TCP/UDP 헤더)

TCP/IP는 OSI 7계층을 4층으로 압축한 실용 버전. 이론(OSI) vs 실제 인터넷(TCP/IP)이라고 기억하면 된다.

# 상위 개념
- [[프로토콜 & 캡슐화]]

# 관련 개념
- [[OSI 모델]]
- [[MAC 주소]]
- [[IPv4 주소 & 클래스]]
- [[ARP]]
- [[ICMP]]
