---
uid: 202603290903
aliases: [ZFW, Zone-Based Policy Firewall, Zone Firewall]
tags: [firewall, security, ios, zfw, zone]
source: RAPA 참고자료 - 260313_Firewall.pdf
created: 2026-03-29
status: complete
---
# 개념
ZFW(Zone-Based Policy Firewall)는 CBAC의 단점(인터페이스 기반 관리의 복잡성)을 보완하여, 라우터의 인터페이스를 **Zone에 할당**하고 Zone 간에 보안 정책을 적용하는 IOS 방화벽 기술이다.

## 핵심 용어
| 용어 | 설명 |
|------|------|
| **Zone** | 보안 정책이 적용되는 인터페이스 그룹 |
| **Zone Member** | Zone에 속한 인터페이스 |
| **Self-Zone** | 시스템 기본 Zone. 라우터 자체가 출발지/목적지인 트래픽 제어 |
| **Zone Pair** | 출발지 Zone과 목적지 Zone의 단방향 묶음 |

## Zone 규칙
- 인터페이스는 **하나의 Zone에만** 소속 가능
- **동일 Zone** 내 인터페이스 간: 기본 **허용**
- **서로 다른 Zone** 간: 기본 **차단** (허용 정책 필요)
- **Self-Zone** ↔ 다른 Zone: 기본 **허용** (차단 정책 필요)
- Zone 미소속 인터페이스는 Zone 소속 인터페이스와 통신 불가
- Zone 멤버 인터페이스에는 ACL, CBAC 적용 불가 (ZFW 정책만 사용)

## 설정 순서

### 1) Zone 생성 및 인터페이스 할당
```bash
zone security inside
zone security outside

interface f0/0
 zone-member security inside
interface f0/1
 zone-member security outside
```

### 2) Zone Pair 생성 (단방향)
```bash
zone-pair security Outbound source inside destination outside
```
- 리턴 트래픽은 Stateful 동작으로 **자동 허용**

### 3) 보안 정책 정의 (ACL + Class-map + Policy-map)
```bash
ip access-list extended acl-outbound
 permit ip any any

class-map type inspect class-outbound
 match access-group name acl-outbound

policy-map type inspect policy-outbound
 class type inspect class-outbound
  inspect
```

### 4) Zone Pair에 정책 적용
```bash
zone-pair security Outbound source inside destination outside
 service-policy type inspect policy-outbound
```

## 확인 명령어
- `show zone security` - Zone 및 멤버 인터페이스 확인
- `show zone-pair security` - Zone Pair 확인
- `show policy-map type inspect zone-pair sessions` - 세션 및 정책 매치 확인

## ZFW와 ACL 관계
- Zone 멤버가 아닌 인터페이스에는 여전히 ACL 적용 가능
- Zone 멤버 인터페이스에 ACL을 직접 적용하면 ZFW 정책과 충돌 → 사용 불가

# 핵심 포인트
- CBAC(인터페이스 기반) → ZFW(Zone 기반)으로 발전하여 관리 용이
- ASA 방화벽과 유사한 Zone 개념을 IOS 라우터에서 구현
- Zone Pair는 **단방향**이지만, Stateful inspect로 리턴 트래픽 자동 허용

# 상위 개념
- [[Firewall]]

# 관련 개념
- [[Firewall CBAC]]
- [[ACL]]
- [[ASA]]
