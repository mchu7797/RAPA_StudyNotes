---
uid: 202602030900
aliases: [Campus Network, 계층적 네트워크 설계, Access Layer, Distribution Layer, Core Layer, 3-Tier]
tags: [network-design, campus, hierarchical, layer2, layer3]
source: 260203_네트워크_이론_7_네트워크_디자인.pdf
created: 2026-02-03
status: complete
---
# 개념
캠퍼스 네트워크는 하나 이상의 건물에 걸친 엔터프라이즈 LAN. Cisco의 계층적 3-Layer 설계(Access/Distribution/Core)를 사용해 확장성·유지보수성·고가용성을 확보한다.

# 핵심 포인트
- **계층적 네트워크 설계 3계층**
  - **Access Layer**: 최종 사용자 장치 연결 (PC, 노트북, AP). 포트 많은 저렴한 L2 스위치, PoE 지원 필요
  - **Distribution Layer**: Access Layer 통합, Core와 연결. L3 라우팅 가능 스위치, 충분한 Bandwidth 필요
  - **Core Layer**: 네트워크 백본, 모든 Distribution 트래픽 처리. 고대역폭·처리량, HA/이중화(이중 전원, 이중 모듈)
- **3가지 트래픽 흐름 패턴**
  1. 동일 Access 스위치, 같은 VLAN 호스트 간 → Access 내부
  2. 서로 다른 Access 스위치 호스트 간 → Distribution 거침
  3. 서로 다른 층/건물 호스트 간 → Distribution → Core 거침
- **이중화 설계 요구사항**
  - 각 Layer: 한 쌍의 스위치 (이중화)
  - 각 스위치에서 상위 Layer로 **두 개의 링크** 연결
  - Distribution 스위치 간 인터링크 필요 (L3 라우팅용)
  - Access 스위치 간 인터링크 불필요
  - VLAN을 Distribution 위(Core)로 확장 금지 → Distribution 이상은 L3 동작
- **Switch Block**: Distribution + Access 쌍으로 구성, 확장 시 블록 단위로 추가

3단 물류창고처럼: Access(현장 작업자) → Distribution(팀장, 부서 통합) → Core(본사, 전체 트래픽 처리). 확장·유지보수·고가용성을 갖춘 설계.

# 상위 개념
- [[네트워크 기초]]

# 관련 개념
- [[VLAN]]
- [[802.1Q Trunk]]
- [[LAN Switching]]
- [[IP 라우팅]]
