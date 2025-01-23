# [컴퓨터네트워크] 7. Circuit Switching과 Packet Switching

<aside>

# 💖 Curcuit Switching

</aside>

## Circuit Switching이란?

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%207%20Circuit%20Switching%E1%84%80%E1%85%AA%20Packet%20Swi%201843f66f522580deb11dca6cf4a7a322/image.png)

- Node들이 **회선을 미리 예약해서 사용**하는 방식입니다.
- 이 때 자원(회선) 할당을 누군가가 관리해야 하기 때문에 **중앙 제어가 필수**적입니다.
    - 전화수가 받아서 전화를 연결해주던 시절에 이 방식이 사용되었습니다.

## Curcuit Switching을 구현하는 방법 2가지

### ⚡️ TDM(Time Division Multiplexing)

시간선을 time slot으로 나누어서 양끝단의 switch를 서로 syncronize합니다. time slot 여러개가 모여 frame을 이룹니다.

### ⚡️ FDM(Frequency Division Multiplexing)

Analog 신호는 서로 다른 대역폭을 사용합니다. 이 점을 이용하여 하나의 회선으로 여러 대역폭의 신호를 동시에 보냅니다.

<aside>

# 💖 Packet Switching

</aside>

## Packet Switching이란?

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%207%20Circuit%20Switching%E1%84%80%E1%85%AA%20Packet%20Swi%201843f66f522580deb11dca6cf4a7a322/image%201.png)

- Packet의 header에는 그 packet의 destination에 관한 정보가 적혀 있습니다.
- router들이 packet의 destination address를 보고 임의로 다음 router를 골라 전송합니다.
    - 따라서 중앙제어가 필요하지 않습니다.

## Circuit Switching VS Packet Switching

|  | Circuit Switching | Packet Switching |
| --- | --- | --- |
| 장점 | 품질은 확실하다. 섞일 일 x |  |
| 단점 | 자원들끼리 경쟁해야 한다. 중앙에서 누군가 관리해야 한다. |  |

## Internet에서 Packet Switching의 과정

1. 각 host의 IP가 Packet을 생성합니다.
2. 이 packet을 router로 전달합니다.
    - 이 때 그 router를 `gateway`라고 합니다.