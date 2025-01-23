# [컴퓨터네트워크] 43. Adress Resolution Protocol (ARP)

<aside>

# 💖 MAC Address

</aside>

## MAC 주소란?

<aside>

**Medium Access Control(MAC) Address** 

기기마다 부여되는 일종의 주민등록번호. Ethernet으로 phisically connected된 interface들 사이에서 주소를 구분함.

</aside>

기기의 ROM에 저장되어 있으며, 대체로 변하지 않습니다.

<aside>

**ROM**

Read Only Memory

</aside>

### MAC 주소의 예시

1A-2F-BB-76-09-AD

## Layer 관점에서의 MAC 주소

| 3계층 | 2계층 |
| --- | --- |
| IP 주소 이용 | MAC 주소 이용 |

<aside>

# 💖 ARP

</aside>

## ARP란?

<aside>

**Address Resolution Protocol(ARP)** 

logical address(IP주소)를 physical address(MAC 주소)로 변환하는 protocol

</aside>

## ARP의 동작 방식

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2043%20Adress%20Resolution%20Protocol%20(A%201843f66f5225806d8a47ead40ddcd75f/image.png)

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2043%20Adress%20Resolution%20Protocol%20(A%201843f66f5225806d8a47ead40ddcd75f/image%201.png)

Broadcast 주소를 이용합니다. 모든 IP 주소들에게 요청을 보낸 후 원하는 한 기기에게 답장을 받습니다.

- 이렇게 Broadcast했을 때, Direct delivery일 경우에는 destination 주소가 돌아올 것이고 Indirect delivery라면 router의 주소가 돌아올 것입니다.

## ARP cache

Caching을 위해 IP주소와 MAC 주소를 짝지어 둔 table을 미리 가지고 있습니다.

- 이 기록은 대부분 20분 정도 유지됩니다.

### 예시

```bash
Linux% arp -a
printer.home (10.0.0.4) at 00:0A:95:87:38:6A [ether] on eth1
gw.home (10.0.0.1) at 00:0D:66:4F:60:00 [ether] on eth1
```

## Gratuitous ARP

<aside>

**Gratuitous ARP** 

불필요한 ARP. 자기 자신의 주소로 ARP request를 보내는 것

</aside>

### 예시

```bash
tcpdump -e -n arp
0:0:c0:6f:2d:40 ff:ff:ff:ff:ff:ff arp 60:
arp who-has 10.0.0.56 tell 10.0.0.56
```

위와 같이 **자기 자신의 주소로 ARP request**를 보냅니다.

### 왜 필요한가요?

- **IP주소가 중복되는 경우가 있는지** 확인하기 위함입니다.
    - 같은 network 안에 동일한 IP 주소가 두 개 이상 있는 경우 network 충돌이 일어남
- let other hosts update the ARP cache entry accordingly

## Routing to Another Subnet

<aside>

**꼭 손으로 하나하나 써 보면서 공부하라고 말씀하심**

</aside>