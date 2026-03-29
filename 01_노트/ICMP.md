---
uid: 202601120908
aliases: [Internet Control Message Protocol, Ping, ICMP]
tags: [icmp, layer3, troubleshooting, ping]
source: 260112_네트워크_이론.pdf
created: 2026-01-12
status: complete
---
# 개념
네트워크 연결성 테스트와 오류 메시지 전달에 사용되는 프로토콜. IP 패킷에 캡슐화되지만 L3 프로토콜로 간주된다.

# 핵심 포인트
- **Ping 유틸리티**: ICMP Echo Request / Echo Reply를 이용해 네트워크 연결성 확인
- **Cisco Ping 응답 기호**
  - `!` : 에코 응답 성공 수신 → L3 연결 정상
  - `.` : 응답 대기 시간 만료 → 경로 상의 연결성 문제
  - `U` : Destination Unreachable → 라우터가 목적지 경로 모르거나 호스트 없음
- **루프백 Ping** (`ping 127.0.0.1`): 호스트 내부 TCP/IP 구성 정상 여부 테스트
- **게이트웨이 Ping**: 라우터 인터페이스 동작 테스트 → 실패 시 외부 네트워크 통신 불가
- ICMP는 IP 패킷에 캡슐화 → L4처럼 보이지만 중요한 IP 프로토콜이므로 **L3 프로토콜**로 간주

"살아있니?"하고 물어보고 "응!"하고 대답하는 것. 네트워크 기초 진단 도구. Ping = ICMP Request/Reply.

# 상위 개념
- [[TCP-IP 모델]]

# 관련 개념
- [[ARP]]
- [[IP 라우팅]]
- [[Default Gateway]]
