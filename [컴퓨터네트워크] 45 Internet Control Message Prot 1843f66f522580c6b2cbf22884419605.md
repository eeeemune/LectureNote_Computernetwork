# [컴퓨터네트워크] 45. Internet Control Message Protocol (ICMP)

<aside>

# 💖 Internet Control Message Protocol (ICMP)

</aside>

<aside>

**개념적으로 중요한 건 맞지만 디테일한 부분을 다 외울 필요가 없다고 하심. 존재와 역할만 파악하면 된다고 하심**

</aside>

## ICMP

앞서 우리는 TTL이 0이 되면 그 packet을 버리고 해당 사실을 host에게 알려 준다고 배웠습니다. 그런데, 이렇게 router에서 error가 발생했을 때 해당 사실을 host에게 어떻게 알려줄 수 있는 걸까요? 이 때 **host와 router가 network layer에서 통신하는 방식**이 ICMP(Internet Communication Message Protocol)입니다.

## ICMP의 format

### 기본 메시지 포맷

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2045%20Internet%20Control%20Message%20Prot%201843f66f522580c6b2cbf22884419605/image.png)

### ICMP의 datafield

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2045%20Internet%20Control%20Message%20Prot%201843f66f522580c6b2cbf22884419605/image%201.png)

위와 같이 헤더와 8byte의 data field가 있습니다.

## ICMP message types

<aside>

**아래 말고는 디테일한 부분을 파악할 필요는 없다고 하심**

</aside>

### ⚡ Time Exceeded

시간 초과. TTL 값이 모두 소진되었다는 정보입니다.

### ⚡ ICMP redirect message

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2045%20Internet%20Control%20Message%20Prot%201843f66f522580c6b2cbf22884419605/image%202.png)

Host로 하여금 **다음부터는 자신이 아니라 다른 router로 자신의 packet을 보내도록**하는 것입니다.

- 예를 들어, HostA가 router R1으로 packet을 보냈다고 합시다.
- 이 상황에서, R1에서는 해당 packet이 자신이 아니라 R2로 가는 것이 좋다고 판단될 수 있습니다.
- 이 때 packet이 R1을 거쳐서 R2로 가는 것보다는 A에서 바로 R2로 보내는 것이 효율적일 것입니다.
- 위와 같은 상황에서 **다음부터는 자신이 아니라 다른 router로 해당 packet을 보내도록 message를 전달**하는 것입니다.

### ⚡ Traceroute

ICMP의 활용입니다. ICMP를 활용하면 어떤 network의 내부 구조를 파악할 수 있습니다. direct delivery로 보낼 수 있는 router들을 모두 출력합니다.

### Stopping criteria

- UDP segment를 보냄
- destination이 `port unrecheable` message를 보냄
- 그러면 source가 stop함
- 만약 ICMP message가 source에 도착했을 때, RTT값을 기록해 둠