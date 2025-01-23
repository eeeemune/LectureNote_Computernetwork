# [컴퓨터네트워크] 26. TCP Sliding Window

<aside>

# 💖 TCP Sliding Window

</aside>

## Sliding Window의 도입 배경

TCP에서 **Reliable한 data 통신**을 하기 위해 채택한 방법. 생각해 보면, TCP에서는 애초에 `NAK` 같은 정보를 recieve하지 않는다. header에는 `ACK` 에 대한 정보밖에 없었다… **이 때 TCP는 어떻게 Go-back-N 방식을 발전시켜서 ARQ를 구현했을까?** 

## Byte-oriented, Sender-side Sliding Window Protocol

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2026%20TCP%20Sliding%20Window%201843f66f522580298e14dcdc8833ff2b/image.png)

TCP는 segment 단위가 아니라 **byte 단위로 정보를 보낸다**

### 그림을 이해해보자…

1. Category #1
    1. 이미 ACK까지 받은 부분 → 이제 신경 쓸 필요 없음
2. **Category 2: Send Window**
    1. 보냈지만, 아직 ACK를 받지 못한 부분
        1. 다시 보내야 할 수도 있으므로 buffer에 저장해 두어야 함
3. **Category 3: Usable Window**
    1. receiver에서 받을 준비는 되어 있지만 내가 아직 보내지 않은 부분
        1. recieiver에서 받을 준비가 되어 있다는 것은 receiver의 buffer에 여유 공간이 남아있다는 의미
4. Category #4
    1. 보내지도 않았고, receiver에서 받을 준비도 안 된 부분

### 시나리오 1: Time out

![IMG_9740.jpeg](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2026%20TCP%20Sliding%20Window%201843f66f522580298e14dcdc8833ff2b/IMG_9740.jpeg)

## Sliding Window Size의 결정

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2026%20TCP%20Sliding%20Window%201843f66f522580298e14dcdc8833ff2b/image%201.png)

위의 그림에서 보듯이, `Sliding Window`의 size는 다음의 buffer 크기를 합한 값이다.

1. 보냈지만, 아직 ACK를 받지 못한 부분
2. receiver에서 받을 준비는 되어 있지만 내가 아직 보내지 않은 부분