---
uid: 202602230020
aliases: [Neighbor 조건]
tags: [network, routing, ospf, neighbor]
source: RAPA 수업 (2/23)
created: 2026-02-23
status: complete
---
하이라이트된 요소들은 필수 조건임.
### Router ID
- 인접 라우터를 구분하기 위한 고유 ID
### ==Hello, Dead Time==
- Hello 메시지 전송 주기
- 인접 장비의 Dead 선언 시간
### ==Area ID==
- 라우터가 속한 Area
### Router Priority
- DR/BRD 선출을 위한 우선 순위 (DR/BDR 선출 환경)
### DR/BDR IP
- DR과 BDR의 IP (DR/BDR 선출 환경)
### ==Authentication Password==
- 안전한 Neighbor 관계 성립을 위해 인증 설정 (Option)
### ==Stub Area Flag==
- Stub란, Area와 다른 유형의 Area로, 동일한 Stub Area에 속해야 Neighbor 가능(Option)
# 나만의 언어로

# 상위 개념
- [[OSPF Neighbor]]