---
uid: 202603290905
aliases: [ASA ACL, ASA Object Group, ASA Access List]
tags: [firewall, security, asa, acl, object-group]
source: RAPA 참고자료 - 260313_Firewall.pdf
created: 2026-03-29
status: complete
---
# 개념
ASA에서의 ACL은 IOS ACL과 유사하게 L2/L3/L4 정보를 분석하여 트래픽을 제어한다. 대규모 환경에서의 관리 편의를 위해 **Object Group**을 사용하여 개체를 그룹화할 수 있다.

## ASA ACL

### IOS ACL과의 차이
- ACL 적용 시 **Global Config Mode**에서 인터페이스 번호 대신 **nameif** 사용
- ACL 삭제 시 `no` 명령어로 전체 삭제 불가 → `clear configure access-list` 사용
- Security Level보다 **ACL이 우선** 적용

### Extended ACL 설정
```bash
! Inside에서 Outside로 HTTP 차단 (High→Low이지만 ACL 우선)
access-list INSIDE_INBOUND deny tcp any host 192.168.2.2 eq 80
access-list INSIDE_INBOUND permit ip any any
access-group INSIDE_INBOUND in interface INSIDE

! Outside에서 DMZ으로 Telnet 허용 (Low→High 예외)
access-list OUTSIDE_INBOUND permit tcp any host 192.168.3.3 eq 23
access-group OUTSIDE_INBOUND in interface OUTSIDE
```

### ACL 편집
```bash
! 특정 위치에 규칙 추가
access-list ALL_OUTBOUND line 3 extended deny tcp any any

! 특정 규칙 삭제
no access-list ALL_OUTBOUND line 3 extended deny tcp any any

! ACL 전체 삭제
clear configure access-list MY_ACL
```

## Object Group
대규모 환경에서 수십 개의 호스트/서버/포트를 개별 ACL로 관리하기 어려우므로, **Object Group으로 그룹화**하여 ACL을 단순화한다.

### Object Group 종류
| 타입 | 용도 |
|------|------|
| **network** | IP 주소, 네트워크 그룹화 |
| **service** | 포트 번호 그룹화 |
| **icmp-type** | ICMP 타입 그룹화 |
| **protocol** | 프로토콜 그룹화 |

### Network Object Group
```bash
! AS-IS: 서버마다 개별 ACL (5줄)
access-list HTTP_TO_DMZ permit tcp any host 192.168.3.1 eq 80
access-list HTTP_TO_DMZ permit tcp any host 192.168.3.2 eq 80
...

! TO-BE: Object Group으로 1줄
object-group network WEB_SERVERS
 network-object host 192.168.3.1
 network-object host 192.168.3.2
 network-object host 192.168.3.3
 network-object host 192.168.3.4
 network-object host 192.168.3.5

access-list HTTP_TO_DMZ permit tcp any object-group WEB_SERVERS eq 80
```

### Service Object Group
```bash
! 여러 포트를 하나로 그룹화
object-group service WEB_SERVICES tcp
 port-object eq 22
 port-object eq 23
 port-object eq 80
 port-object eq 443

! Network + Service Object Group 조합
access-list HTTP_TO_DMZ permit tcp any object-group WEB_SERVERS object-group WEB_SERVICES
```

## 확인 명령어
- `show access-list [ACL이름]` - ACL 상세 및 매치 수 확인
- `show run | include [ACL이름]` - ACL 설정 확인

# 핵심 포인트
- ASA ACL은 **nameif 기반** 적용, `clear configure`로 삭제
- Object Group으로 **IP/포트를 그룹화**하면 ACL 관리가 획기적으로 단순화
- Network + Service Object Group을 **조합**하여 복잡한 정책도 간결하게 표현

# 상위 개념
- [[ASA]]

# 관련 개념
- [[ACL]]
- [[ASA NAT]]
- [[Firewall]]
