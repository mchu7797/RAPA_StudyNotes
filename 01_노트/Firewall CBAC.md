---
uid: 202603290902
aliases: [CBAC, Context-Based Access Control, IOS Firewall]
tags: [firewall, security, ios, cbac]
source: RAPA 참고자료 - 260313_Firewall.pdf
created: 2026-03-29
status: complete
---
# 개념
CBAC(Context-Based Access Control)은 Cisco IOS 라우터에서 **Stateful 방화벽** 기능을 제공하는 기술이다. L3/L4뿐 아니라 **응용계층(L7) 트래픽까지 제어** 가능하다.

## 동작 원리
1. 내부에서 외부로 나가는 패킷을 inspect
2. 돌아오는 패킷을 허용하는 **임시 ACL 자동 생성**
3. 기존 ACL이 있다면 임시 ACL이 우선 적용
4. 패킷 처리 완료 후 임시 ACL 삭제

## Basic CBAC 설정

### 정책 결정
- 외부 → 내부: 모든 트래픽 차단
- 내부 → 외부: TCP, UDP, ICMP 패킷의 리턴만 허용

### 설정 순서
```bash
! 1) 외부 인터페이스에 deny all ACL 적용
ip access-list extended outside-acl-in
 deny ip any any
interface f0/1
 ip access-group outside-acl-in in

! 2) CBAC inspect 설정 (나가는 방향)
ip inspect name Outside-outbound tcp
ip inspect name Outside-outbound udp
ip inspect name Outside-outbound icmp
interface f0/1
 ip inspect Outside-outbound out
```

### 결과
- 내부 → 외부: ping, telnet 등 정상 동작 (임시 ACL이 리턴 허용)
- 외부 → 내부: 여전히 모두 차단

## Application CBAC
- 특정 애플리케이션만 선별 허용 가능
- 예: HTTP만 허용하고 나머지 TCP 차단

```bash
ip inspect name mycbac http audit-trail on
interface f0/0
 ip inspect mycbac in
```
- `audit-trail on`: 해당 패킷의 로그 출력
- HTTP(포트 80)만 돌아오는 트래픽 허용, Telnet 등은 차단

## 확인 명령어
- `show ip inspect sessions detail` - 현재 inspect 세션 확인

# 핵심 포인트
- CBAC은 라우터에서 **전용 방화벽 없이** Stateful Inspection 구현
- 임시 ACL을 동적 생성/삭제하여 리턴 트래픽 자동 허용
- 단점: 인터페이스 기반이라 **다수 인터페이스 시 관리 복잡** → ZFW로 대체

# 상위 개념
- [[Firewall]]

# 관련 개념
- [[ACL]]
- [[Firewall ZFW]]
- [[Cisco IOS]]
