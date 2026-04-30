---
uid: 202604301611
aliases: [Thin-Client SSL VPN]
tags: [ssl-vpn, remote-access, security]
source: RAPA 참고자료 - SSL VPN.pdf
created: 2026-04-30
status: complete
---
# 개념
Thin-Client SSL VPN은 웹 외 일부 애플리케이션(예: SSH, 메일 등)까지 확장 지원하는 SSL VPN 방식이다.

## 동작 방식
- 최소 에이전트/플러그인으로 필요한 프로토콜만 터널링
- 전체 트래픽 터널이 아니라 정책 기반 앱 단위 접근에 가깝다

## 장점
- Clientless보다 확장성 좋고, Full Tunnel보다 통제 범위가 명확
- 운영자가 "허용할 애플리케이션 집합"을 단계적으로 설계하기 좋음

## 한계
- 지원 프로토콜/클라이언트 버전에 따라 호환성 이슈 가능
- 단말 OS 업데이트 후 에이전트 동작 문제가 발생할 수 있음

# 핵심 포인트
- Clientless와 Full Tunnel 사이의 중간 모델이다.
- 필요한 기능만 제공해 운영 복잡도와 접근 범위를 조절하기 좋다.

# 상위 개념
- [[SSL VPN]]

# 관련 개념
- [[SSL VPN Clientless]]
- [[SSL VPN Tunnel Mode (AnyConnect)]]

