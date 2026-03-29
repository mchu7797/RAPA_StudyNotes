---
uid: 202603290904
aliases: [ASA, Adaptive Security Appliance, Cisco ASA]
tags: [firewall, security, asa, cisco]
source: RAPA 참고자료 - 260313_Firewall.pdf
created: 2026-03-29
status: complete
---
# 개념
ASA(Adaptive Security Appliance)는 Cisco의 **전용 방화벽 제품**으로, 방화벽 외에도 VPN 등 여러 보안 기능을 탑재한 장비이다. 소규모 환경에서는 IOS 방화벽으로 충분하지만, 대규모 네트워크에서는 성능과 기능 면에서 전용 방화벽이 필요하다.

## CLI Mode
| 모드 | 프롬프트 | 진입 명령 |
|------|---------|----------|
| User EXEC | `ciscoasa>` | 기본 |
| Privileged EXEC | `ciscoasa#` | `enable` |
| Global Config | `ciscoasa(config)#` | `configure terminal` |
| Specific Config | `ciscoasa(config-if)#` | 인터페이스 등 진입 |

## 동작 모드
- **Router Mode (L3)**: 기본 모드. 라우팅 가능
- **Transparent Mode (L2)**: 브릿지처럼 동작
- 전환: `firewall transparent` / `no firewall transparent`
- 확인: `show firewall`

## Security Level
ASA의 핵심 개념. 각 인터페이스의 **신뢰도**를 숫자로 표현한다.

| Security Level | 용도 | nameif 기본값 |
|---------------|------|--------------|
| **100** (최고) | Inside | `inside` → 자동 100 |
| **50** (중간) | DMZ | `dmz` → 수동 지정 필요 |
| **0** (최저) | Outside | `outside` → 자동 0 |

### 트래픽 규칙
- **High → Low**: 기본 허용
- **Low → High**: 기본 거부 (ACL 예외 필요)
- **동일 Level**: 기본 거부
- Security Level보다 **ACL이 우선 적용**됨

### 인터페이스 설정 예시
```bash
interface E0/0
 nameif INSIDE
 security-level 100
 ip address 192.168.1.254 255.255.255.0
 no shutdown

interface E0/1
 nameif OUTSIDE
 security-level 0
 ip address 192.168.2.254 255.255.255.0
 no shutdown

interface E0/2
 nameif DMZ
 security-level 50
 ip address 192.168.3.254 255.255.255.0
 no shutdown
```

## 라우팅
```bash
! Static Route (nameif 사용)
route outside 0.0.0.0 0.0.0.0 1.1.40.2

! OSPF (서브넷 마스크 사용, 와일드카드 아님)
router ospf 1
 network 10.1.1.0 255.255.255.0 area 0
 default-information originate
```

## SSH 접속 설정
```bash
username admin password cisco123
aaa authentication ssh console LOCAL
crypto key generate rsa modulus 1024
ssh 10.10.10.1 255.255.255.255 inside
ssh 1.1.10.1 255.255.255.255 outside
```

## ASDM (GUI 관리)
ASA의 GUI 관리 도구. 웹 브라우저로 접속하여 설정/모니터링.
```bash
asdm image disk0:/asdm-731.bin
http server enable
http 192.168.1.0 255.255.255.0 INSIDE
username ADMIN password PASSWORD privilege 15
```

## 설정 저장
- `copy run start` 또는 `write memory`
- 초기화: `write erase`

## 확인 명령어
- `show nameif` - 인터페이스 이름 및 Security Level
- `show ip address` - IP 주소 확인
- `show interface ip brief` - 인터페이스 상태 요약
- `show firewall` - 동작 모드 확인
- `show version` - OS, 업타임, 하드웨어 정보

# 핵심 포인트
- ASA는 **Security Level**로 Zone 간 신뢰도를 설정하여 트래픽 제어
- IOS와 유사하지만 **nameif**, **security-level** 등 ASA 고유 문법 사용
- OSPF 설정 시 와일드카드 마스크가 아닌 **서브넷 마스크** 사용

# 상위 개념
- [[Firewall]]

# 관련 개념
- [[ASA ACL & Object Group]]
- [[ASA NAT]]
- [[ASA Failover]]
- [[ACL]]
- [[Cisco IOS]]
