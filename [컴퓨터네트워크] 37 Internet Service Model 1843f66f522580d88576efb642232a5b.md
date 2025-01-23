# [컴퓨터네트워크] 37. Internet Service Model

<aside>

# 💖 Network service model

</aside>

<aside>

**Internet이 왜 best effort service인지는 이해하고 있어야 한다고 말씀하심**

</aside>

## Internet service model

Internet은 `Best effort service`입니다. **최선을 다하겠지만 결과는 보장하지 않는다**는 의미입니다. 과연 Interenet은 어떤 것에 최선을 다하고 어떤 결과를 보장하지 않는다는 걸까요?

### best effort service

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2037%20Internet%20Service%20Model%201843f66f522580d88576efb642232a5b/image.png)

1. Loss: 중간에 **Datagram의 Loss가 없음**을 보장하지 않습니다.
    - successful datagram delivery to destination
2. Order: **데이터가 순차적으로 전달**됨을 보장하지 않습니다.
    - bandwidth available to end-end flow
3. Timing: **데이터가 원하는 시간 내에 도착**함을 보장하지 않습니다.
    - timing or order of delivery