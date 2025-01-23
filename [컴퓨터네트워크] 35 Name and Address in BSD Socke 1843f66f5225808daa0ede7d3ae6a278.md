# [컴퓨터네트워크] 35. Name and Address in BSD Socket

<aside>

# 💖 Address and Name in BSD Sockets API

</aside>

## Internet에서 Address와 Name

### Name

겹칠 수 있습니다. 사람이 쉽게 부르고 이해하기 위해서 사용되기 때문에 address에 비해 긴 이름을 사용하고, 공간을 좀 낭비해도 됩니다.

### Address

겹칠 수 없습니다. 짧은 이름을 사용하고, 특정 format으로 이루어져 있습니다.

## IPv4 Address

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2035%20Name%20and%20Address%20in%20BSD%20Socke%201843f66f5225808daa0ede7d3ae6a278/image.png)

- memory의 byte level에서 이걸 어떻게 저장할 것인가? 가 중요한 topic이 됩니다.

### network byte order vs host byte order

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2035%20Name%20and%20Address%20in%20BSD%20Socke%201843f66f5225808daa0ede7d3ae6a278/image%201.png)

- Network byte order는 보통 `big-endian`으로되어있지만, host byte order는 보통 `little-endian`으로 이루어져 있습니다.
    - 이 때 변환이 필요합니다.

## Resolution

- Resolution: name → address
- 이 때, 무조건 1:1 대응이 되는 것은 아닙니다.
    - 하나의 이름이 여러 개의 IP address를 가질 수도 있습니다.
    - 여러 이름이 하나의 IP address를 가질 수도 있습니다.

<aside>

# 💖 References

</aside>

https://velog.io/@hsshin0602/%EC%BB%B4%ED%93%A8%ED%84%B0-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-TCP-Timer