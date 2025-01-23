# [컴퓨터네트워크] 17. Connection-oriented

<aside>

# 💖 Connection

</aside>

# Transport Layer Basics

## Connection-oriented demultiplexing

- TCP/IP가 여기에 속한다고 한다

## 네트워크에서의 Connection

- source 와 destination의 **주소와 port를 특정하는 것이 중요**하다
- 이 네 가지가 확실해지면 메시지 여러 개가 섞이지 않게 각각 전송할 수 있다

### Connectionless

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2017%20Connection-oriented%201843f66f522580f1b23dee9c32725d03/image.png)

port가 특정되어있지 않아서 packet을 하나의 창구로 보낸다.

- 이렇게 되면 이걸 demultiplexing하는 것은 application 개인의 몫…

### Connection-Oriented

- TCP/IP가 여기에 속한다고 한다