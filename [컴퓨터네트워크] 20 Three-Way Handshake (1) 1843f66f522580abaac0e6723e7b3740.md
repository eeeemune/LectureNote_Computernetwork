# [컴퓨터네트워크] 20. Three-Way Handshake (1)

<aside>

# 💖 Connection Establishment

</aside>

TCP에서 server와 clinet 간의 연결 수립 과정에 대해서 배웁니다.

<aside>

# 💖 Three-Way Handshake

</aside>

<aside>

**Three way handshake**

TCP에서 server와 client 사이 연결을 확립하는 과정. 서로 상대방이 데이터를 받을 준비가 되었음을 알 수 있다.

</aside>

## TCP Packets

### ⚡ SYN

Synchronize Sequence Number. ‘연결해주세요’라는 신호라고 볼 수 있습니다.

### ⚡ ACK

Acknowledgement. ‘연결되었습니다’라는 신호라고 볼 수 있습니다.

### ⚡ seq

buffer의 시작 주소. Server와 client에서 각각 이 sequence number가 동기화 됩니다.

- 맨 처음 sequence number는 **임의의 ISN**으로 정해집니다.

### ⚡ ack

상대방이 다음에 보내주길 원하는 seq number.

### ⚡ rwnd

recieve window. 내가 받을 수 있는 buffer의 크기를 indicate합니다.

- `ack`가 활성화 되어있는 상태에서 유효합니다.

## Three-Way Handshake의 연결 수립

<aside>
🚨

**TCP는 왜 굳이 3-way handshake 방식을 사용하나요?**

물론 2-way로도 사용이 가능하지만, 3-way handshake가 더 안정성 있음이 이론적으로 알려졌기 때문입니다.

</aside>

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2020%20Three-Way%20Handshake%20(1)%201843f66f522580abaac0e6723e7b3740/image.png)

- **Step 1 (SYN)**
    
    **클라이언트는 서버와 커넥션을 연결하기 위해 SYN을 보낸다. (seq : x)**
    
    - 송신자가 최초로 데이터를 전송할 때 Sequence Number를 임의의 랜덤 숫자로 지정하고, SYN 플래그 비트를 1로 설정한 세그먼트를 전송한다.
    - PORT 상태
        - Client : `CLOSEDSYN_SENT` 로 변함
        - Server : `LISTEN`
- **Step 2 (SYN + ACK)**
    
    **서버가 SYN(x)을 받고, 클라이언트로 받았다는 신호인 ACK와 SYN 패킷을 보냄 (seq : y, ACK : x + 1)**
    
    - 접속요청을 받은 Q가 요청을 수락했으며, 접속 요청 프로세스인 P도 포트를 열어달라는 메세지를 전송 (SYN-ACK signal bits set)
    - ACK Number필드를 Sequence Number + 1 로 지정하고 SYN과 ACK 플래그 비트를 1로 설정한 새그먼트 전송 (`Seq=y, Ack=x+1, SYN, ACK`)
    - PORT 상태
        - Client : `CLOSED`
        - Server : `SYN_RCV`
- **Step 3 (ACK)**
    
    **클라이언트는 서버의 응답은 ACK(x+1)와 SYN(y) 패킷을 받고, ACK(y+1)를 서버로 보냄**
    
    - 마지막으로 접속 요청 프로세스 P가 수락 확인을 보내 연결을 맺음 (ACK)
    - 이때, 전송할 데이터가 있으면 이 단계에서 데이터를 전송할 수 있다.
    - PORT 상태
        - Client : `ESTABLISED`
        - Server : `SYN_RCV` ⇒ ACK ⇒ `ESTABLISED`
    
    <aside>
    🚨
    
    **seq flag가 왜 8000에서 8001로 늘어났나요?**
    
    SYN flag가 켜져 있기 때문입니다. 이 SYN이 1을 소모합니다. 반면, ACK flag는 따로 seq number를 소모하지 않습니다.
    
    </aside>
    

## 일반적인 상황에서 TCP의 데이터 Communication

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2020%20Three-Way%20Handshake%20(1)%201843f66f522580abaac0e6723e7b3740/image%201.png)

1. `Push` flag: 최대한 빨리 처리해주세요.
2. **`ACK`** flag
    1. 15001번이라는 사실을 알 수 있다. ack가 15001번이 된 후  server가 또 보내 온 정보가 없기 때문이다.

## Connection Termination

![마지막 segment에서 교수님이 seq를 x+1로 고쳐 두셨는데, 본인이 실수한 것 같다고 말씀하심…… 그러면서 이런 seq num의 detail은 별로 안 중요해서 무시해도 된다고 말씀하심.](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2020%20Three-Way%20Handshake%20(1)%201843f66f522580abaac0e6723e7b3740/image%202.png)

마지막 segment에서 교수님이 seq를 x+1로 고쳐 두셨는데, 본인이 실수한 것 같다고 말씀하심…… 그러면서 이런 seq num의 detail은 별로 안 중요해서 무시해도 된다고 말씀하심.

1. client → server `FIN` flag를 전달합니다.
2. server → client `FIN + ACK` flag를 전달합니다.
    1. 이 과정은 필수적이지 않습니다. client에서 server로 전송할 데이터는 이제 없지만 **server에서 client로 전송할 데이터는 남아 있는 경우**에는 FIN flag를 보내지 않을 수 있다.
3. client → server `ACK` flag 전달. `FIN` flag를 잘 받았음을 알림.

<aside>
🚨

**Active close와 Passive close는 어떻게 다른가요?**

**먼저 close를 요청했다면 active**, 아니라면 passive가 됩니다. 그래서 경우에 따라서는 server가 active close를 할 수도 있습니다.

</aside>

<aside>

# 💖 References

</aside>

https://velog.io/@averycode/네트워크-TCPUDP와-3-Way-Handshake4-Way-Handshake