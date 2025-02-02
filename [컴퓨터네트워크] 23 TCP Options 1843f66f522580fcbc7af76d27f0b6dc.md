# [컴퓨터네트워크] 23. TCP Options

<aside>

# 💖 Timeout of Connection Establishment

</aside>

<aside>

**분량이 많다고 해서 시험에 나올 것이다,,, 라고 생각하지 말라고 말씀하심. 그냥 말씀하시는 것 중 요점만 기억하라고 하심. 이 부분은 시험에 거의 안 나올 수도 있다고 말씀하심.**

</aside>

## Timeout의 도입 배경

**TCP 요청을 보냈는데 상대방의 응답이 없다면** 임의로 connection을 termination하는데, 얼마나 기다릴지를 `timeout`으로 미리 세팅해 둘 수 있습니다.

<aside>

# 💖 TCP Options

</aside>

## Options

<aside>

**option을 전부 외울 필요는 없지만, 중요한 option은 기억하고 가야 한다고 말씀하심. 이 네 개의 option 중에서 1개가 시험문제로 나올 거라고 말씀하심. 교수님께서 어떤 부분을 중요하다고 생각하실 것 같은지 잘 알아 맞춰 보라고 말씀하심.**

</aside>

- TCP header의 뒷부분 혹은 data의 앞부분에 **option을 붙여서 보낼 수 있습니다.**

## 중요한 Options

### ⚡ MSS

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2023%20TCP%20Options%201843f66f522580fcbc7af76d27f0b6dc/image.png)

MAX Segment Size. **내가 받을 수 있는 Data의 최대 크기**를 알립니다.

- 이름은 segment size지만 data의 크기를 상한합니다.
- network interface 별로 packet의 size가 다르기 때문에, 그 **interface가 가질 수 있는 packet의 max size**를 적어 두는 것입니다.
    - 예를 들어, ethernet은 1500으로 정해져 있습니다.

### ⚡ WSOPT

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2023%20TCP%20Options%201843f66f522580fcbc7af76d27f0b6dc/image%201.png)

- TCP Header 부분에는 `rwnd` field가 있습니다.
    - `receive window`: 내가 받을 수 있는 buffer의 최대 크기를 명시하는 field
- 그런데 `rwnd` field는 size가 겨우 16bit밖에 안 됩니다.
    - 이 부분을 보 완하기 위해서 WSCALE(WSOPT)가 도입되었습니다.
- 2^n을 곱해 준다고 하는데, 어떤 건지는 잘 모르겠다. 따로 살펴봐야 할 듯,,,
- **SYN Segment를 보낼 때만 전달할 수 있다** !!
- **connection이 established될 때 fix된다. 연결 도중에 바꿀 수 없다 !! !! !!**

### ⚡ SACK

- Selective ACK
- TCP에서, 전송 중간에 **오류가 생겼을 경우 어떤 게 손실이 되었는지** 알려줄 수 있는 ACK를 제공.
    - 이게 SACK라고 한다.
- 오류가 발생했을 때 처음부터 다시 통신하는 게 아니라 손실된 부분만 다시 전송하다 보니 속도가 빠르다.
- 하나하나 설명을 하자면 시간이 길어져서 그림으로까지 설명하지는 않겠다고 말씀하심

### ⚡ TSOPT

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2023%20TCP%20Options%201843f66f522580fcbc7af76d27f0b6dc/image%202.png)

- timestamp.
- sequence number는 32bit이다.
- 아주 빠른 네트워크의 경우, sequence number가 너무 빨리 소모된다.
    - 1초면 다 돌아버린다고…
- 이럴 경우 buffer에 같은 번호를 갖는 packet이 여러 개 생길 수도 있다.
- 이럴 때 각 packet을 `TSOPT`을 통해 구별할 수 있다.

## Path MTU Discovery with TCP (Optional)

- 현업에서 사용하는 일종의 skill이라고 한다. 그냥 넘어가심