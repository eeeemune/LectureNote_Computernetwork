# [컴퓨터네트워크] 04. Protocol Data Units(PDU)

## Protocol Data Units(PDU))

### PDU의 탄생 배경

- 위에서 살펴봤듯이, layer마다 data unit을 부르는 이름이 통일되어있지 않습니다.
    - 예를 들어, layer 2에서는 frame, 3에서는 packet, 4에서는 segment…
- OSI에서는 이러한 이름들을 통합하야 하나의 명칭으로 부르길 원했습니다.
- 등장한 data unit의 이름이 `PDU`입니다.
    - PDU는 Protocol Data Unit의 약자입니다.

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2004%20Protocol%20Data%20Units(PDU)%201843f66f522580a3ac1af481cdfdd707/image.png)