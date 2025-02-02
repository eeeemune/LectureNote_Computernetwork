# [컴퓨터네트워크] 03. OSI Reference Model

## Reference Model이란 무엇인가요?

<aside>

**Reference Model**

타의 모범이 되는, 다른 곳에서도 따서 따라 쓸 수 있는 model

</aside>

## OSI Reference Model이란 무엇인가요?

<aside>

**OSI Reference Model**

ISO에서 개발한 Network Layering model.

</aside>

- ISO에서 layer를 나눌 때 이렇게 나누면 좋지 않을까? 하고 제시한 model.

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2003%20OSI%20Reference%20Model%201843f66f522580dcb018de5dd856aff9/image.png)

## ⚡ Layer 1: Physical Layer

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2003%20OSI%20Reference%20Model%201843f66f522580dcb018de5dd856aff9/image%201.png)

통신의 최하위 부분에 위치한 Layer로, 물리적인 부분을 담당합니다. **오직 데이터를 전송하는 기능만 담당하기 때문에, 오류를 제어하지 않습니다.**

- 예를 들어, bit의 voltage가 몇일 때 1이고 몇일 때 0인가? 등에 관한 규약이 있습니다.
- 케이블, repeater, Hub등이 이에 해당합니다.

## ⚡ Layer2: Data link layer

하나의 컴퓨터 네트워크를 구축할 정도로 본격적인 레이어입니다.

<aside>
🚨

 **Data link layer는 reliable하지 않은 전송이에요.**

</aside>

<aside>

**Reliablity**

어떤 전송이 `reliable`하다는 것은 정보를 전송했을 때 **오류가 생겼을 경우 수신측에서 그 문제를 자체적으로 결정하여 처리**한다는 의미입니다.

</aside>

### Service

Data link layer는 framing을 수행합니다.

- **Framing**
    
    <aside>
    
    **Framing**
    
    데이터 stream의 어느 부분이 시작점이고 어느 부분이 끝점인지 표시하는 것
    
    </aside>
    
    <aside>
    
    **Q. Framing은 어떤 방식으로 이루어지나요?**
    
    Header와 Trailer 앞뒤로 `Preemble`이라는 bit pattern을 삽입합니다. 이를 통해 데이터의 시작과 끝을 알 수 있게 됩니다.
    
    </aside>
    

### MAC이란?

<aside>

**MAC address**

하드웨어마다 부여되는 고유 번호

</aside>

## ⚡ Layer3: Network layer

`packet`이라고 하는 데이터를 상위 계층으로 보내는 것을 목표로, **어느 경로로 보내야 하는가?**를 결정합니다.

### Fragmentation

- Node A, B가 통신을 할 때 서로 다른 기술을 사용할 수도 있습니다.
- 이 때 Network Layer는 **내가 사용하는 기술의 전송 단위에 따라 적절히 data를 encoding**합니다.
- 이를 `Fragmentation`이라고 합니다.

### Packet scheduling

Network Layer에서는 `port`를 통해 router의 buffer에 도착한 packet들을 어떤 순서로 전송할지 결정하는 역할을 합니다.

- 이 때, 각 packet들 사이에는 우선순위가 존재합니다.
- router와 port
    - `router`에는 `buffer`가 있고, 이 buffer 안에 전송될 packet들이 대기하고 있습니다.
    - 이 packet들은 `port`를 통해 전송됩니다.

## ⚡ Layer4: Transport Layer

**Transport layer에서는 `multiplexing`을 담당**합니다.

- 각 node에는 이미 여러개의 process들이 돌아가고 있고, packet을 적절한 process에 전달해야만 합니다.
- 이 때 Transport layer는 packet들을 multiplexing하여 적절한 process에게 전달합니다.

## ⚡ Layer5: Session Layer

- 동기화를 담당하는 Layer입니다.
- OSI model 중 하나이긴 하지만, 실제로 session layer가 명시적으로 사용되는 경우는 거의 없습니다.
    - 요즘은 이 session layer 대신 그냥 자체적인 library를 사용하는 추세라고 합니다.

<aside>

 **Session**

일정 시간동안 어떠한 상태를 유지하는 것

</aside>

## ⚡ Layer6: Presentation Layer

- data format을 변환하여 상위 레이어에 전달합니다.

## ⚡ Layer7: Application Layer

- 말 그대로 응용 프로그램들을 놓는 계층입니다.
- SSH, HTTP 등의 protocol을 사용합니다.

<aside>

# 💖 OSI Refernece Model

</aside>

## Intermediate Node

<aside>

**Intermediate Node**

source와 destination node가 아닌, 중간에서 통신만 담당하는 node.

</aside>

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2003%20OSI%20Reference%20Model%201843f66f522580dcb018de5dd856aff9/image%202.png)

1, 2, 3번 layer간의 통신에는 `Intermediate node`가 필요합니다.

- physical하게 연결되어야 하기 때문입니다.
- 예를 들어 Network layer끼리 통신해야 한다면, physical layer→Data link layer→Network layer 순서로 data가 전달됩니다.
- 나머지 4, 5, 6, 7 layer는 `intermediate node`가 없이도 layer-to-layer communication이 가능합니다.