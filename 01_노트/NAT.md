---
uid: 202601140902
aliases: [NAT, Network Address Translation, Static NAT, Dynamic NAT, PAT, Overload NAT]
tags: [nat, ipv4, routing, addressing]
source: 260114_네트워크_이론_2.pdf
created: 2026-01-14
status: complete
---
# 개념
사설 IP 주소와 공인 IP 주소 간에 주소를 변환하는 기술. IPv4 주소 고갈 문제를 해결하고 사설 네트워크의 내부 호스트가 인터넷과 통신할 수 있게 한다.

# 핵심 포인트
- **NAT 배경**: IPv4 주소(약 43억 개)가 고갈 → 사설 IP 주소를 이용하고 외부와 통신 시 공인 IP로 변환
- **주로 라우터(또는 방화벽)에 구현**, 가정용 공유기에도 적용
- **Inside Local**: 사설 네트워크 내부 호스트 IP (사설 주소)
- **Inside Global**: 외부(인터넷)에 보이는 공인 IP 주소

---

### Static NAT
- 사설 IP 1개 ↔ 공인 IP 1개 **1:1 고정 매핑**
- 서버처럼 외부에서 고정 IP로 접근해야 하는 경우 사용
- `ip nat inside source static [사설IP] [공인IP]`

### Dynamic NAT
- 공인 IP Pool에서 사설 IP에 동적으로 공인 IP 할당 (1:1, 선착순)
- 공인 IP Pool이 소진되면 추가 변환 불가

### PAT (Port Address Translation) / NAT Overload
- **가장 일반적인 방식** (가정용 공유기 등)
- 사설 IP 다수 → 공인 IP 1개(또는 소수)로 **포트 번호로 구분**
- 하나의 공인 IP로 수만 개의 사설 호스트 동시 인터넷 접속 가능
- `ip nat inside source list [ACL번호] interface [외부인터페이스] overload`

### NAT 동작 원리 (PAT 기준)
```
[내부 호스트]                  [NAT 라우터]                  [인터넷]
192.168.1.10:1234  →  공인IP:60001 (포트 변환 후 전달)  →  서버
                   ←  공인IP:60001 (응답 수신)          ←  서버
192.168.1.10:1234  ←  포트 기반 역변환하여 내부 호스트에 전달
```

# 나만의 언어로
<!-- 이 개념을 누군가에게 설명한다면? 비유, 요약, 한 줄 정리 등 -->
아파트 단지 전체가 하나의 공인 IP를 쓰는 것. 건물 내부 주소(사설 IP)는 바깥에서 모르지만, 경비실(라우터)이 포트 번호로 누가 누구인지 기억하며 패킷을 전달한다.

# 상위 개념
- [[IPv4 주소 & 클래스]]

# 관련 개념
- [[IP 라우팅]]
- [[Default Gateway]]
