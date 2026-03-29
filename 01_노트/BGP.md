---
uid: 202602230008
aliases: [Border Gateway Protocol]
tags: [network, routing, routing-protocol, egp, bgp]
source: RAPA 수업 (2/23)
created: 2026-02-23
status: complete
---
# 개념
BGP(Border Gateway Protocol)는 **AS 간 라우팅을 담당하는 유일한 EGP 프로토콜**이다. 인터넷의 핵심 라우팅 프로토콜로, ISP 간 또는 대규모 조직 간 경로 정보를 교환한다. 단순한 최단 경로 대신 **정책 기반 경로 선출(Path Vector)** 을 사용한다.

## eBGP vs iBGP

| 항목 | eBGP | iBGP |
|------|------|------|
| 동작 범위 | 서로 다른 AS 간 | 동일 AS 내부 |
| AD 값 | 20 | 200 |
| TTL | 1 (직접 연결 기본) | 255 |
| Next-Hop 변경 | 자동 변경 | 변경 안 함 (Next-Hop-Self 필요) |
| Full-Mesh 요구 | 없음 | 기본적으로 필요 (또는 RR/Confederation) |

## BGP 주요 특징
- **TCP 179 포트** 사용 → 신뢰성 있는 연결 기반
- Path Vector 방식 → AS-PATH 속성으로 루프 방지
- 수동으로 Neighbor 지정 (`neighbor` 명령어)
- 경로 수렴이 느림 → 안정성 우선

## BGP 테이블 구조
BGP는 라우팅 테이블과 별도로 **BGP 테이블**을 유지한다.
- `>` : Best Path (라우팅 테이블에 등록되는 경로)
- `*` : Valid (유효한 경로)
- `i` : iBGP로 학습한 경로

## 기본 설정 (Cisco IOS)
```bash
router bgp [AS 번호]
 neighbor [IP] remote-as [상대 AS 번호]
 network [네트워크] mask [서브넷 마스크]
```

# 핵심 포인트
- BGP는 **인터넷의 라우팅 프로토콜** — AS 간 경로 교환 담당
- eBGP: AS 간 / iBGP: AS 내부 → 용도가 다름
- 정책 기반 제어 (AS-PATH, LOCAL_PREF, MED 등 다양한 속성 활용)

# 상위 개념
- [[EGP]]

# 관련 개념
- [[BGP eBGP & iBGP]]
- [[BGP Neighbor 상태]]
- [[BGP 메시지 타입]]
- [[BGP Path Vector]]
- [[BGP 테이블]]
- [[BGP Advertisements]]
- [[BGP Network Advertise]]
- [[BGP Next-Hop-Self]]
- [[BGP Confederation]]
