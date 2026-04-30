---
uid: 202604301610
aliases: [WebVPN, Clientless SSL VPN]
tags: [ssl-vpn, webvpn, remote-access, security]
source: RAPA 참고자료 - SSL VPN.pdf
created: 2026-04-30
status: complete
---
# 개념
Clientless SSL VPN은 웹 브라우저만으로 사내 리소스에 접속하는 SSL VPN 방식이다.

## 특징
- 설치형 클라이언트 없이 URL 접속만으로 사용 가능
- 포털 기반으로 허용된 웹 애플리케이션 링크 제공
- 사용자 경험은 좋지만 네트워크 레벨 전체 접근에는 한계

## 적합한 사용 사례
- 외부 협력사/단기 사용자에게 제한된 웹 시스템 접근 제공
- 관리형 단말이 아닌 환경(BYOD)에서 최소 권한 접근

## 주의할 점
- 웹이 아닌 프로토콜(일부 전용 앱)은 직접 지원이 어렵다
- 브라우저 보안(캐시, 다운로드 파일, 세션 타임아웃) 정책이 중요
- 세션 탈취 방지를 위해 MFA + 짧은 세션 만료 정책 권장

# 핵심 포인트
- 별도 VPN 클라이언트 설치 없이 빠르게 접속할 수 있다.
- 웹 기반 업무 시스템 접근에 특히 유리하다.
- 전체 네트워크 터널링보다는 애플리케이션 접근 게이트웨이 성격이 강하다.

# 상위 개념
- [[SSL VPN]]

# 관련 개념
- [[SSL VPN Thin-Client]]
- [[SSL VPN Tunnel Mode (AnyConnect)]]

