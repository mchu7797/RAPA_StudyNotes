# 방법 1 : auto-cost 설정을 사용해 reference bandwidth를 설정한다.
```

R1(config-router)#auto-cost reference-bandwidth ?

<1-4294967> The reference bandwidth in terms of Mbits per second


R1(config-router)#auto-cost reference-bandwidth 10000
```
# 방법 2 :  특정 인터페이스의 ospf cost를 변경한다.
```
R3(config)#int gi 0/1/0
R3(config-if)#ip ospf cost 191
```
# 상위 개념
- [[OSPF Metric]]
- [[OSPF]]