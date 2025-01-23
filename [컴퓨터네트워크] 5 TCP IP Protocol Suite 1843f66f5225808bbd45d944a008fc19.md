# [컴퓨터네트워크] 5. TCP/IP Protocol Suite

## Protocol layering 복습

### Protocol layering은 왜 필요한가요?

- 필요한 이유
    1. 하위 layer를 abstract하게 만들어서 훨씬 단순하게 다룰 수 있습니다.
    2. layering을 사용하면 **각 과정들을 sequencial하게 진행**할 수 있습니다.
    3. invariance를 보장할 수 있습니다.
    
    <aside>
    
      **Invariant**
    
    어떤 통신이 invariant하다면, source node에서 n번째 layer의 message는 destination node의 n번째 layer에서도 동일하다
    
    </aside>
    
    ![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%205%20TCP%20IP%20Protocol%20Suite%201843f66f5225808bbd45d944a008fc19/image.png)
    

## TCP/IP Protocol Suite

![image.png](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%205%20TCP%20IP%20Protocol%20Suite%201843f66f5225808bbd45d944a008fc19/image%201.png)

TCP/IP의 Protocol Stack model입니다. OSI model에서의 일부 레이어들을 통합한 형태입니다.

![우리 교재에서는 이렇게 5계층으로 나눈다고 하심](%5B%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%B2%E1%84%90%E1%85%A5%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%5D%205%20TCP%20IP%20Protocol%20Suite%201843f66f5225808bbd45d944a008fc19/image%202.png)

우리 교재에서는 이렇게 5계층으로 나눈다고 하심