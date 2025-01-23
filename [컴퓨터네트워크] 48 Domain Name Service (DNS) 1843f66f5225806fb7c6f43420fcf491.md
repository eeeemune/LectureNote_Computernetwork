# [컴퓨터네트워크] 48. Domain Name Service (DNS)

<aside>

# 💖 Domain Name Service

</aside>

<aside>

**DNS zone과 Domain의 차이는 관심 있는 사람만 찾아 보라고 하심**

</aside>

## Top-Level Domain

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2048%20Domain%20Name%20Service%20(DNS)%201843f66f5225806fb7c6f43420fcf491/image.png)

## Internet Assigned Numbers Authority

.com, .org 등의 top level domain을 관리하고 부여하는 기관들입니다.

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2048%20Domain%20Name%20Service%20(DNS)%201843f66f5225806fb7c6f43420fcf491/image%201.png)

### Delegation record

이 TLD를 어디에서 관리하는지가 적혀있습니다. 예를 들어, `.kr`같은 경우에는 한국 인터넷 진흥원에서 관리한다는 사실을 알 수 있습니다.

## DNS Zone

DNS server를 두고 name과 IP 주소의 mapping을 관리하는 기관이 필요함.

## DNS Records

<aside>

**이 Type들을 꼭 기억하라고 하심**

</aside>

distributed database에는 `resource records`들이 저장되어 있습니다. `RR`이라고도 합니다.

### 기본 포맷

<aside>

**RR format: (name, value, type, ttl)** 

</aside>

### Type=A

| **name** | hostname |
| --- | --- |
| **value** | IP address |

### Type=NS

해당 hostname의 주소를 관장하고 있는 nameserver가 어디인지를 알아야 합니다. authoritative name의 hostname을 가지고 있습니다.

- 예를 들어, 내가 foo.com이라는 domain을 가비아에서 구매했다면 nameserver는 gabia.com이 됩니다.

| **name** | domain |
| --- | --- |
| **value** | authoritative name의 hostname |

### Type=CNAME

별명과 원래 이름의 대응을 가지고 있습니다.

| **name** | **(alias name)** 별명 |
| --- | --- |
| **value** | (canonical name) 진짜 이름 |

### Type=MX

mail exchanger. 해당 도메인과 연동되어있는 메일서버를 확인하는 데에 사용합니다.

- 이를 통해 **해당 도메인을 이메일 주소로 사용**하는 것을 가능케 합니다.

## DNS Protocol

<aside>

**디테일한 부분은 시험에 안 낼 거라고 말씀하심**

</aside>

query message와 reply message가 있고, 같은 format을 가지고 있습니다.

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%2048%20Domain%20Name%20Service%20(DNS)%201843f66f5225806fb7c6f43420fcf491/image%202.png)

<aside>

# 💖 References

</aside>

https://inpa.tistory.com/entry/WEB-%F0%9F%8C%90-DNS-%EB%A0%88%EC%BD%94%EB%93%9C-%EC%A2%85%EB%A5%98-%E2%98%85-%EC%95%8C%EA%B8%B0-%EC%89%BD%EA%B2%8C-%EC%A0%95%EB%A6%AC#mx_mail_exchanger