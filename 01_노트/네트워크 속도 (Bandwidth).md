---
uid: 202601160901
aliases: [Bandwidth, 대역폭, bps, 인터넷 속도, 네트워크 속도]
tags: [bandwidth, speed, layer1]
source: 260116_네트워크_이론_3_속도.pdf
created: 2026-01-16
status: complete
---
# 개념
네트워크 속도는 단위 시간당 전송 가능한 비트(bit) 수로 측정하며, 이를 대역폭(Bandwidth)이라 한다.

# 핵심 포인트
- **단위**: bps (bit per second), 초당 전송 비트 수
- **bit vs Byte**
  - bit: 데이터 **전송 속도(대역폭)** 표현 기준
  - Byte: **파일 크기·데이터 양(용량)** 표현 기준
  - 1 Byte = 8 bit / 1 KByte = 8,000 bit / 1 MByte = 8,000,000 bit / 1 GByte = 8,000,000,000 bit
- 속도 향상 = **더 넓은 대역폭** (차선 비유: 넓은 차선 = 같은 시간에 더 많은 데이터 전달)
- **인터페이스 대역폭**
  - FE (FastEthernet): 100 Mbps
  - Gi (GigabitEthernet): 1000 Mbps (1 Gbps)
  - Ten (TenGigabitEthernet): 10 Gbps
- `show interfaces` 명령에서 BW (Kbit 단위)로 대역폭 확인 가능
- 계산 예시: 490 Mbps ≈ 초당 약 61 MByte 파일 전송 가능

차선(대역폭)이 넓을수록 같은 시간에 더 많은 차(데이터)가 이동한다. bit는 속도, Byte는 양이라는 단위 구분이 중요하다.

# 상위 개념
- 

# 관련 개념
- [[NIC & 케이블]]
- [[Cisco IOS]]
