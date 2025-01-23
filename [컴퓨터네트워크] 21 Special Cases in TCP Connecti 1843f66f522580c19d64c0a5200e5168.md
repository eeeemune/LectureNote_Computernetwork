# [컴퓨터네트워크] 21. Special Cases in TCP Connection Management

## TCP Connection에서의 예외 케이스

1. Simultaneous Open
2. TCP Half-Close
3. Simultaneous Close

## ⚡ Simultaneous Open

<aside>

**디테일한 부분은 굳이 설명하지 않겠다고 말씀하심**

</aside>

두 app이 **완전히 동시에 연결을 시도**했을 경우, TCP는 3-way가 아니라 `4-way handshake`를 수행하게 된다.

### TCP Hole Punching

`Simultaneous Open` 을 이용하면 이런 것들까지 가능한데, 관심 있는 사람만 찾아 보라고 말씀하심.

## ⚡ TCP Half-Close

이것도… 그렇게까지 중요한 부분은 아니고, 이런 게 있다는 정도만 알아 두라고 말씀하심

## ⚡ Simultaneous Close

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2021%20Special%20Cases%20in%20TCP%20Connecti%201843f66f522580c19d64c0a5200e5168/image.png)

이렇게 FIN이 엇갈려도 잘 처리해야 한다고 말씀하심.