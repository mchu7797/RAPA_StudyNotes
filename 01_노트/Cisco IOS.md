---
uid: 202601160900
aliases: [Cisco IOS, IOS 명령어, CLI, Cisco OS]
tags: [cisco, ios, cli, configuration]
source: 260116_네트워크_이론_3.pdf
created: 2026-01-16
status: complete
---
# 개념
Cisco IOS(Internetwork Operating System)는 대부분의 Cisco 엔터프라이즈급 네트워크 장비에서 사용하는 운영 체제.

# 핵심 포인트
- **Cisco OS 종류**: IOS(기본), NX-OS(Nexus/MDS), IOS-XR(ASR9K), IOS-XE(ASR1K)
- **장비 접속**: 초기 설정은 콘솔(Console) 케이블 연결 필요 (IP 미설정 상태)
- **명령어 계층 구조 (Hierarchy)**
  - `hostname>` : User EXEC mode
  - `hostname#` : Privileged EXEC mode (`enable` 입력)
  - `hostname(config)#` : Global Configuration mode (`configure terminal`)
  - `hostname(config-if)#` : Interface Configuration mode (`interface x`)
  - `exit`: 한 단계 하위 복귀 / `end`: 모든 수준에서 Exec 모드로 즉시 복귀
- **단축 명령어(약어)**: 유일하게 일치하는 경우에만 사용 가능 (예: `en` = `enable`)
- **Context Help**: `?` 입력으로 사용 가능한 명령어·옵션 확인
- **Config 저장 위치**
  - Flash: IOS 이미지 저장
  - NVRAM: Startup Configuration (부팅 시 자동 로드)
  - RAM: Running Configuration (현재 동작 중인 설정, 재부팅 시 소멸)
- **설정 저장**: `copy running-config startup-config` 또는 `write memory`
- **공장 초기화**: `wr erase` 또는 `erase startup-config` → `reload`
- **show 명령어 필터**: `| begin`, `| include`, `| exclude`, `| section`

# 나만의 언어로
<!-- 이 개념을 누군가에게 설명한다면? 비유, 요약, 한 줄 정리 등 -->
Cisco 장비는 계층적 CLI로 설정한다. Running config는 RAM에 있어 재부팅하면 사라짐 → 반드시 `wr` 로 NVRAM에 저장해야 한다.

# 상위 개념
- 

# 관련 개념
- [[스위치 기본 설정]]
- [[IP 라우팅]]
