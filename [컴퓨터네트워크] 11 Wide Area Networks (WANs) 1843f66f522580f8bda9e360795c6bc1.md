# [컴퓨터네트워크] 11. Wide Area Networks (WANs)

<aside>

# 💖 Wide Area Networks (WANs)

</aside>

Ethernet 등은 기본적으로 근거리 통신을 위한 기술입니다.

- 보통 하나의 건물 정도를 커버합니다.
- 장거리 통신을 위한 기술이 따로 있는데, 이러한 기술들을 묶어서 WAN이라고 합니다.

<aside>

**WAN**

Wide Area Networks. 장거리 통신을 위한 기술들의 묶음

</aside>

## WAN 기술들

1. Cable-based access
2. Digital subscriber line
3. Cellular networks

## ⚡ Cable-based access

**shared** cable을 이용해 FDM 방식으로 통신합니다.

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2011%20Wide%20Area%20Networks%20(WANs)%201843f66f522580f8bda9e360795c6bc1/image.png)

- 예전에 원룸 등에서 케이블 TV용으로 많이 사용했다고 합니다.
    - 지금은 IPTV가 대세여서 잘 없지만 그래도 여전히 많이 볼 수 있다고 합니다

### frequency division multiplexing (FDM)

cable based access WAN은 `FDM` 방식으로 multiplexing합니다.

### Hybrid Fiber Coax

<aside>

**HFC**

Hybrid Fiber Coax. **optical fiber과 coaxial cable을 합한 형태.**

</aside>

cable access network를 구현하기 위해 사용되는 **물리적 cable**들입니다.

| **Fiber Optic Cable** | **coaxial cable** |
| --- | --- |
| 지역 대 지역 | 지역 내 |
- 그 유명한,,, 동축케이블이 이거라고 말씀하심

## ⚡ Digital subscriber line (DSL)

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2011%20Wide%20Area%20Networks%20(WANs)%201843f66f522580f8bda9e360795c6bc1/image%201.png)

- **이미 존재하는** 전화선으로 고속 인터넷을 사용할 수 있는 기술입니다.
- 쌍방향은 아니고,,, 다운로드 속도만 빠릅니다.
    
    
    | **Upstream** | Downstream |
    | --- | --- |
    | 3.5-16 Mbps | 24-52 Mbps |

## ⚡ Cellular networks

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2011%20Wide%20Area%20Networks%20(WANs)%201843f66f522580f8bda9e360795c6bc1/image%202.png)

- 주로 휴대전화에 사용되는 기술입니다.
- `Cellular`는 지역 별로 **구획을 나눠서** 통신을 중계하는 기술입니다.
    - 무선 휴대전화를 이용하다 보면 기지국이 통신을 중계합니다.
    - 하지만 이 기지국은 길어야 1km정도밖에 영향을 못 미칩니다.
    - 그래서 지역을 cell 단위로 구획하여 통신을 중계합니다.
        - 우리나라의 이동 통신 3사는 이런 걸,,, 하는 것입니다.
- **4세대부터는 celluer 기술 전체가 다 `TCP/IP` protocol을 이용합니다.**