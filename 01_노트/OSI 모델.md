---
uid: 202601120904
aliases: [OSI Model, Open System Interconnection, 7계층 모델]
tags: [osi, model, fundamental]
source: 260112_네트워크_이론.pdf
created: 2026-01-12
status: complete
---
# 개념
1977년 ISO가 데이터 전송 과정을 7계층으로 분류한 참조 모델. 실무보다 네트워크 통신 과정을 개념적으로 설명하는 데 활용된다.

# 핵심 포인트
- **Layer 7 Application**: 이메일, 웹, FTP 등 서비스
- **Layer 6 Presentation**: 데이터 포맷·구조화 (JPEG, MPEG, ASCII)
- **Layer 5 Session**: 두 호스트 간 연결 설정·관리·종료
- **Layer 4 Transport**: 신뢰성 확인, 재전송, 애플리케이션 식별 (TCP / UDP)
- **Layer 3 Network**: 다른 네트워크 전달, 라우팅 (IPv4, IPv6)
- **Layer 2 Data Link**: 같은 네트워크 내 전달, 오류 감지 (이더넷)
- **Layer 1 Physical**: 비트 신호를 전기·빛·전파로 전달
- 상위 3계층 (5~7): **애플리케이션 개발자** 영역
- 하위 4계층 (1~4): **네트워크 엔지니어** 영역
- 계층은 건너뛸 수 없음 → 데이터 전송 시 항상 모든 계층을 거쳐야 함

# 나만의 언어로
<!-- 이 개념을 누군가에게 설명한다면? 비유, 요약, 한 줄 정리 등 -->
7층 건물에서 엘리베이터를 타는 것과 같다. 보낼 때는 7층→1층, 받을 때는 1층→7층으로 이동하며 각 층에서 자기 역할을 수행한다.

# 상위 개념
- [[프로토콜 & 캡슐화]]

# 관련 개념
- [[TCP/IP 모델]]
- [[MAC 주소]]
- [[IPv4 주소 & 클래스]]
