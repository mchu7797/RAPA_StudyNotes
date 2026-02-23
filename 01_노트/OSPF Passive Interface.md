# 개념
- 특정 인터페이스에 [[OSPF]] Hello 패킷 전송을 막기 위해 사용하는 기능
- 말단(호스트)장비와 연결되는 인터페이스에 주로 적용함
	- BPDU Guard와 그 용도와 역할이 비슷함.
# 설정 방법
```
Router(config)#router ospf 1
Router(config-router)#passive-interface ? # ?의 내용을 인터페이스 명칭으로 치환
```
# 상위 개념
- [[OSPF]]
# 유사 개념