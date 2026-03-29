---
uid: 202603180253
aliases: [Access Control List, Standard ACL, Extended ACL]
tags: [acl, security, ipv4, routing]
source: RAPA 수업 (3/10) - Security ACL
created: 2026-03-18
status: complete
---
# 개념
ACL(Access Control List)은 라우터/스위치에서 트래픽을 **허용(permit) 또는 차단(deny)** 하기 위한 규칙 집합이다.

- 패킷 필터링(Filtering)
- 특정 트래픽 분류(Classification)
- VTY 라인 접근 제어(Telnet/SSH 제한) 등에 활용

## 동작 원리
- ACL은 **Top-Down** 으로 순차 평가된다.
- 규칙에 매칭되면 즉시 permit/deny가 결정된다.
- 끝까지 매칭되지 않으면 마지막의 **implicit `deny any`** 에 의해 차단된다.

## 종류
### Standard ACL
- 검사 기준: **Source IP**
- 번호 범위: `1-99`, `1300-1999`
- 일반적으로 **목적지에 가까운 위치**에 배치

### Extended ACL
- 검사 기준: **Source IP + Destination IP + L4 포트/프로토콜**
- 번호 범위: `100-199`, `2000-2699`
- 일반적으로 **출발지에 가까운 위치**에 배치

## 와일드카드 마스크
- 서브넷 마스크의 반대 개념
- 예: `192.168.1.0 0.0.0.255` (192.168.1.0/24 대역 매칭)
- 단일 호스트: `host 192.168.1.10`
- 전체 매칭: `any`

## 기본 설정 예시
```bash
access-list 1 permit 192.168.12.0 0.0.0.255
interface fa0/0
 ip access-group 1 in
```

## 확인 명령어
- `show access-lists`
- `show ip interface <interface>`

# 핵심 포인트
- ACL은 **순서가 핵심**이다(위에서 아래로 평가).
- 마지막의 `deny any`를 항상 염두에 두고 permit 규칙을 먼저 설계해야 한다.
- Standard/Extended ACL은 검사 범위와 배치 전략이 다르다.


# 상위 개념
- [[IP 라우팅]]

# 관련 개념
- [[NAT]]
- [[Default Gateway]]
