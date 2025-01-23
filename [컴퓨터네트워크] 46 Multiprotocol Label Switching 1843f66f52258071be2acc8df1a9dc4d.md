# [컴퓨터네트워크] 46. Multiprotocol Label Switching (MPLS)

<aside>

# 💖 Multiprotocol label switching (MPLS)

</aside>

## MPLS

### circuit switching과 packet switching

앞서 우리는 여러개의 router가 통신을 하는 방식에는 두 가지가 있다고 배웠습니다.

- Circuit Switching: **회선을 미리 예약**하고, 그 다음 데이터를 exchange하는 방식입니다.
    - 회선을 미리 예약하기 때문에 **데이터의 품질이 보장된다**는 장점이 있습니다.
    - 하지만 그 회선의 예약을 담당하는 **중앙 controller가 존재해야 한다**는 단점이 있습니다.
- packet switching: 각 router들이 판단해서 다음 router를 정하는 방식입니다.
    - 현재는 이 방식이 사용된다고 배웠습니다.
    - packet switching 방식에서, router들은 매번 packet이 도착할 때마다 load balancing을 새로 진행합니다.
    - 이 때 매번 도착하는 packet들을 각자 다른 것으로 인식하다 보니 품질이 보장되기 어렵습니다.

### Virtual Circuit

packet들의 header를 이용하여 packet switching의 단점을 보완하는 방식입니다.

<aside>

**Virtual Circuit** 

Ethernet header 옆에 MPLS header를 붙여서 그 MPLS header에 각 packet의 회선 번호를 저장해 두고, **마치 가상의 회선의 있는 것처럼 생각**함

</aside>

## MPLS가 사용되는 시나리오

아래와 같이 기본적으로 IP를 지원하는 router만 있는 상태라고 상정해 봅시다.

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2046%20Multiprotocol%20Label%20Switching%201843f66f52258071be2acc8df1a9dc4d/image.png)

R6, R5에서 A로의 `traffic`이 존재하는 상황입니다.

<aside>

**Traffic** 

source에서 destination으로 향하는 packet들의 집합

</aside>

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2046%20Multiprotocol%20Label%20Switching%201843f66f52258071be2acc8df1a9dc4d/image%201.png)

이 때, MPLS router인 R4, R3, R2, R1이 중간에 껴있다면?

- `IP/MPLS router`인 R4에서 traffic을 받습니다.
    - R6, R5에서 도착한 packet들이 자신의 source에 따라서 서로 다른 lable을 가지고 있음을 알 수 있습니다.
- **해당 label을 기준으로 가상의 회선이 있는 것처럼 동작**합니다.

## MPLS signaling

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2046%20Multiprotocol%20Label%20Switching%201843f66f52258071be2acc8df1a9dc4d/image%202.png)

curcuit switching에서 `call setup`을 하듯, MPLS를 지원하는 router들 사이에서 미리 자원을 예약하는 것입니다.