---
uid: 202603290906
aliases: [ASA NAT, Object NAT, Manual NAT, Auto NAT]
tags: [firewall, security, asa, nat]
source: RAPA 참고자료 - 260313_Firewall.pdf
created: 2026-03-29
status: complete
---
# 개념
ASA의 NAT는 IOS NAT와 기본 원리는 동일하지만, 더 다양한 종류와 세밀한 주소 변환 정책을 지원한다. **Object NAT(Auto NAT)**과 **Manual NAT** 두 가지 방식으로 구현할 수 있다.

## NAT 종류

| 종류 | 설명 |
|------|------|
| **Static NAT/PAT** | 반영구적 1:1 매핑. 양방향 통신 시작 가능 |
| **Dynamic NAT/PAT** | 트래픽 발생 시 임시 할당. 통신 끝나면 제거(3분). 반대 방향 통신 시작 불가 |
| **Policy NAT/PAT** | 출발지 + 목적지에 따라 변환 주소 결정 |
| **Bypass NAT** | 특정 출발지/목적지 패킷만 주소 변환 제외 |

## Object NAT (Auto NAT)
- 하나의 Network Object 안에서 NAT 정책 설정
- **출발지 주소만** 변환 가능
- 설정이 간단하고 직관적
- 설정 순서와 무관하게 **세부 정책일수록 상위에 자동 등록**

### Dynamic NAT - Object NAT
```bash
! Pool 생성
object network PUBLIC_POOL
 range 192.168.2.100 192.168.2.200

! 변환 대상 정의 + NAT 설정
object network INTERNAL
 subnet 192.168.1.0 255.255.255.0
 nat (INSIDE,OUTSIDE) dynamic PUBLIC_POOL
```

### Dynamic PAT - Object NAT
```bash
object network INSIDE
 subnet 192.168.1.0 255.255.255.0
 nat (INSIDE,OUTSIDE) dynamic interface
```
- `dynamic interface`: ASA 외부 인터페이스 IP로 PAT

### Static NAT - Object NAT
```bash
object network WEB_SERVER
 host 192.168.1.1
 nat (DMZ,OUTSIDE) static 192.168.2.200
```
- 외부에서 접근하려면 **Static NAT + ACL 허용** 모두 필요

## Manual NAT
- 출발지 + 목적지 **모두 참고**하여 주소 변환
- NAT 테이블 순위를 관리자가 **직접 지정** 가능
- Global Config Mode에서 설정

### Static NAT - Manual NAT
```bash
object network inside_real
 host 10.1.1.1
object network inside_mapped
 host 1.1.10.100

nat (inside,outside) source static inside_real inside_mapped
```

### Dynamic NAT - Manual NAT
```bash
nat (inside,outside) source dynamic inside_real inside_mapped destination static outside_real outside_real
```

### Dynamic PAT - Manual NAT
```bash
nat (inside,outside) source dynamic inside_real interface destination static outside_real outside_real
```

## NAT 동작 순서 (우선순위)
1. **Manual NAT - Section 1** (최우선)
2. **Auto NAT - Section 2**
3. **Manual NAT with after-auto - Section 3** (최후순위)

## L2 Mode NAT 제한사항
- `any` 키워드 사용 불가
- 실제 주소와 변환 주소를 반드시 명시
- 인터페이스 PAT 불가 (L2 모드라 인터페이스에 IP 없음)

## 확인 명령어
- `show nat` / `show nat detail` - NAT 정책 및 히트 수
- `show xlate` - 현재 주소 변환 테이블 (실제 변환 내역)

# 핵심 포인트
- **Object NAT**: 간단한 1:1 변환에 적합. 자동 순서 관리(Auto NAT)
- **Manual NAT**: 출발지+목적지 기반 정밀 제어. 관리자가 순서 지정
- Static NAT는 **양방향**, Dynamic NAT/PAT는 **단방향**(내부→외부)
- 외부에서 내부 접근 시 Static NAT + ACL 허용이 모두 필요

# 상위 개념
- [[ASA]]

# 관련 개념
- [[NAT]]
- [[ASA ACL & Object Group]]
- [[Firewall]]
