---
uid: 202603040845
aliases: [BGP Message Type, BGP Messages]
tags: [network, routing, bgp]
source: RAPA 수업 (3/3) - 네트워크 이론 9
created: 2026-03-04
status: draft
---
# 개념
BGP는 TCP(포트 179) 위에서 동작하며 4가지 메시지 타입을 사용한다.

| 메시지 | 역할 |
|--------|------|
| **OPEN** | BGP 세션 수립 요청. AS 번호, Hold Time, BGP Router ID, Optional Parameter(Capability) 포함 |
| **KEEPALIVE** | 세션 유지 확인. Hold Time의 1/3 주기로 전송 (기본 60초마다) |
| **UPDATE** | 경로 정보 전달. 새 경로(NLRI + Path Attributes) 또는 철회할 경로(Withdrawn Routes) 포함 |
| **NOTIFICATION** | 오류 발생 시 상대에게 알리고 세션 종료 |

## OPEN 메시지 주요 필드
- BGP Version (현재 4)
- AS Number (원격 AS 확인에 사용)
- Hold Time (양측 중 낮은 값으로 협상)
- BGP Router ID
- Optional Parameters : 4-byte ASN, Route-Refresh, MP-BGP 등의 Capability 협상

## UPDATE 메시지 주요 필드
- **Withdrawn Routes** : 더 이상 유효하지 않은 경로 목록
- **Path Attributes** : AS_PATH, NEXT_HOP, LOCAL_PREF, MED 등
- **NLRI (Network Layer Reachability Information)** : 광고할 IP prefix

# 핵심 포인트
- BGP는 **증분(Incremental) 업데이트** 방식 → 변경된 경로만 UPDATE로 전송
- Hold Time이 0이면 KEEPALIVE를 보내지 않음 (세션이 만료되지 않음)
- NOTIFICATION 메시지를 받으면 세션이 즉시 Idle 상태로 전환됨

# 나만의 언어로
<!-- 이 개념을 누군가에게 설명한다면? 비유, 요약, 한 줄 정리 등 -->

# 상위 개념
- [[BGP]]

# 관련 개념
- [[BGP Neighbor 상태]]
