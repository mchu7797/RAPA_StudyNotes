---
uid: 202602230018
aliases: []
tags: [network, routing, ospf, config]
source: RAPA 수업 (2/23)
created: 2026-02-23
status: complete
---
```
Router(config)# router ospf [process_id]

Router(config-router)# network [ip-address] [wildcard-mask] area [area-id]
```
# `router ospf ...`
- 한 라우터 내에서 여러 개의 OSPF 프로세스를 동시에 돌릴 수 있음.
- 프로세스를 구분하기 위해서 Process ID라는 구분자를 활용
- 라우터 내부에서만 의미가 있으므로, 다른 라우터와 관계가 없음.
# `network ...`
- Network 키워드는 OSPF 통신을 활성화할 네트워크 대역이나 특정 인터페이스를 지정하겠다는 명령임.
	- 이 명령어에 매칭되는 인터페이스는 OSPF Hello 패킷을 보내기 시작함.
	- 자신의 네트워크 정보를 이웃 라우터에게 광고하게 됨.
- IP Address는 [[OSPF]]를 활성화할 네트워크 주소, 서브넷 주소, 또는 특정 인터페이스의 정확한 IP 주소를 입력해야 함.
	- Wildcard Mask와 결합하여 검사 기준이 됨.
- Wildcard Mask는 서브넷 마스크를 반대로 뒤집은 형태의 마스크임.
	- IP주소의 어떤 부분을 정확히 검사하고 어떤 부분을 무시할지 라우터에게 알려주기 위한 기준
- Area ID는 해당 네트워크가 소속될 OSPF 영역 번호임.
# 나만의 언어로

# 상위 개념
- [[OSPF]]
