# [컴퓨터네트워크] 49. Internet Routing Protocols

<aside>

# 💖 IP Routing Protocols

</aside>

## IP Routing Protocol

오늘 우리가 배울 내용은 IP Routing Protocol입니다. 우리의 목표는 다음과 같습니다.

<aside>

**Router A에서 B로 가는 최소 경로 구하기**

</aside>

## Graph abstraction

우리는 네트워크 과목을 처음 배울 때 이미 네트워크를 그래프의 형태로 나타낼 수 있다고 배웠습니다. 다음 네트워크의 경우 아래와 같이 `node`들과 `edge`들의 집합으로 나타낼 수 있습니다.

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2049%20Internet%20Routing%20Protocols%201843f66f52258093b096c9051b84b04e/image.png)

- Set of Routers
    - { u, v, w, x, y, z }
- Set of links
    - { (u,v), (u,x), (v,x), (v,w), (x,w), (x,y), (w,y), (w,z), (y,z) }

## Routing algorithms의 분류

### ⚡ Global VS Decentralized

|  | Global | Decentralized |
| --- | --- | --- |
| 특징 | **모든 link들의 cost information**을 알고 있음 | neighbors들의 information exchange를 반복함으로서 정보를 알 수 있음 |
| 대표 알고리즘 | Link state algorithm | Distance vector algorithm |

### ⚡ Static VS Dynamic

|  | Static | Dynamic |
| --- | --- | --- |
| 특징 | 경로가 아주 천천히 바뀜 | 경로가 빠르게 바뀜 |

## Autonomous Symstems(AS)

우리는 Internet을 **network들의 network**라고 배웠습니다. 여러 개의 라우터가 네트워크 집합을 이루고 또 그 라우터들의 집합끼리 네트워크를 이루게 됩니다. 이 때 **라우터들의 집합**을 `Domain` 또는 `Autonomous Systems` 라고 하고, 약칭으로 `AS`라고 부릅니다.

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2049%20Internet%20Routing%20Protocols%201843f66f52258093b096c9051b84b04e/image%201.png)

<aside>

# 💖 Intra-AS routing과 Inter-AS routing

</aside>

<aside>

**routing을 어떻게 분류할 수 있는가 등만 기억하면 된다고 하심**

</aside>

## ⚡ Intra-AS Routing Protocols

<aside>

**RIP랑 OSPF, BGP의 이름만 기억하면 된다고 하심**

</aside>

<aside>

**Intra-AS**

같은 AS 안에 있는 router들 사이에서 수행하는 routing

</aside>

- **관리자가 자체적으로 routing**을 할 수 있습니다.
    - 이 routing을 위해서 우리는 특정한 알고리즘을 사용하게 되는데, 이를 `routing protocol`이라고 합니다.
        - routing protocol이 자동적으로 실행되어서 **forwarding table**을 채웁니다.
- Gateway router를 포함합니다.
    
    <aside>
    
    **Gateway Router**
    
    다른 AS와 맞닿아 있는 router
    
    </aside>
    

### 💛 Routing Information Protocol(RIP)

<aside>

**RIP(Routing information Protocol)**

Distance Vector를 기반으로 routing을 수행. router들 간 **주기적으로 거리 정보를 교환.** ‘가장 적은 hops의 수’를 최단 경로로 판단

</aside>

- 최근에는 잘 쓰이지 않는 알고리즘이라고 합니다.

### 💛 Enhanced Interior Gateway Routing Protocol(EIGRP)

<aside>

**EIGRP(Enhanced Interior Gateway Routing Protocol)**

DV 기반으로 동작하지만, link state protocol의 특성을 띔

</aside>

- 원래는 Cisco-proprietary를 위한 기술이었지만 2013년 이후로는 다른 곳에서도 널리 쓰인다고 합니다.

### 💛 Open Shortest Path First(OSPF)

<aside>

**OSPF(Open Shortest Path First)**

link state routing protocol. link state의 정보를 담고 있는 database를 하나 두고, 해당 db를 기반으로 최소 경로를 찾음.

</aside>

## ⚡ Inter-AS routing

<aside>

**Inter-AS**

AS들 사이의 routing. Gateway에서 routing 작업을 수행하게 됨

</aside>

### 💛 BGP

<aside>

**BGP algorithm은 배우지 않는다고 하심**

</aside>

<aside>

# 💖 Routing Algorithms

</aside>

## ⚡ link state algorithm

Dijsktra algorithm을 기반으로 합니다. 실제로 Dijkstra씨가 고안한 알고리즘이라고 합니다.

<aside>

**Link State Algorithm**

centralized한 상황에서 node들을 연결하는 최소 cost를 찾는 알고리즘

</aside>

- 모든 link들의 cost 정보를 미리 알고 있을 경우, 이를 `centralized`하다고 말합니다.

### 예시

<aside>

**손으로 직접 해 보라고 말씀하심**

</aside>

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2049%20Internet%20Routing%20Protocols%201843f66f52258093b096c9051b84b04e/image%202.png)

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2049%20Internet%20Routing%20Protocols%201843f66f52258093b096c9051b84b04e/image%203.png)

### Discussion

- n(n+1)/2 → O(n^2) complexity
- 최대 O(nlongn)

### Dijkstra’s algorithm: oscillations possible

- 모든 router들이 자신의 정보를 알리기 위해 broadcast해야만 함… 따라서
- cost가 변하지 않는다면 문제가 없음
- 하지만 cost가 유동적으로 변한다면?
- 

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2049%20Internet%20Routing%20Protocols%201843f66f52258093b096c9051b84b04e/image%204.png)

## ⚡ Distance vector

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2049%20Internet%20Routing%20Protocols%201843f66f52258093b096c9051b84b04e/image%205.png)

- Bellman-Ford equation을 기반으로 합니다. DP 기반으로 동작합니다.
- mild한 assumption 하에서, **분산적입니다.**
    - 최소값이 어떤 값으로 수렴하게 되는데, Bellman씨는 이를 수학적으로 증명하는 데에 성공하셨다고 합니다.
- iterative하고, **asynchronous**하다는 특징때문에 널리 쓰입니다.

### Bellman-Ford Equation

<aside>

**Dx (y) = minv { cx,v + Dv (y) }**

</aside>

### Good news travels fast

- cost를 감소시킬 수 있는 정보는 바로바로 퍼짐
    - 왜냐하면 작은 값을 업데이트 하게 되기 때문임
- Bad news travels slow
    - 더 느려졌다면 table을 업데이트 안 하고 말기 때문에… 어떤 link의 cost가 더 높아졌다면 해당 사실이 반영되는 것은 매우 느리다

<aside>

# 💖 References

</aside>

https://velog.io/@kimdukbae/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EB%B2%A8%EB%A7%8C-%ED%8F%AC%EB%93%9C-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-Bellman-Ford-Algorithm

⭐ https://10000cow.tistory.com/entry/%EB%B2%A8%EB%A7%8C-%ED%8F%AC%EB%93%9C-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%ED%95%9C-%EC%82%B4%EB%8F%84-%EC%9D%B4%ED%95%B4%ED%95%98%EB%8A%94-%EB%B2%A8%EB%A7%8C-%ED%8F%AC%EB%93%9C-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98Bellman-Ford-Algorithm