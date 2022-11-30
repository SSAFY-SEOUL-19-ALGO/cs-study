# IP 주소체계, IPv4, IPv6

## ✒︎ IP 주소 체계

### ✢ IPv4에서의 주소 체계

![IPv4주소형식](https://github.com/devjunmo/TIL/raw/main/img/IP/IPv4%EC%A3%BC%EC%86%8C.png)
- 총 32bit를 8bit 단위(옥텟)로 점을 찍어 네개 덩어리로 표현
- 2^32개의 주소를 표현하므로 41억 9천만의 주소 표현 가능하며, 현대에는 부족한 숫자이므로 NAT이나 서브네팅등 부수적인 기술이 필요함


### ✢ IPv6에서의 주소 체계

![IPv6주소형식](https://github.com/devjunmo/TIL/raw/main/img/IP/IPv6%EC%A3%BC%EC%86%8C.png)
- 총 128bit를 16bit씩 8개로 구분하여 표현 (2^128개 주소 표현 가능)
- 16비트는 16진수로 변환되어 콜론으로 구분하여 표시
- NAT나 서브네팅이 필요하지 않음
- 앞의 64bit는 Network portion, 뒤의 64bit는 interface 주소


### ✢ IPv4 header
![IPv4 header](https://github.com/devjunmo/TIL/raw/main/img/IP/IPv4_header.png)

- Version
    - 인터넷 프로토콜의 버전을 저장
- IHL(Internet Header Length)
    - IP 헤더의 길이를 나타낸다
    - 주로 최소값인 5를 쓰며, 5 × 32 bits = 160 bits = 20 bytes이다
    - 6이상이면 options에 뭔가가 추가된것
- TOS(Type of Service)
    - 패킷의 전송 우선순위를 지정한다
- Identification
    - 단편화과정(MTU보다 큰 데이터가 왔을때 쪼개어 받은 후 재조립 하는 과정)에서 송신 호스트가 지정하는 구분자. 수신측에서 해당 필드를 통해 재조립 할수 있도록 한다.
- flags
    - 3bit flag
        - 첫번째 비트는 항상0
        - 두번째 비트는 DF(don’t fragment?)
            - 분할된 패킷이면 1, 아니면 0
        - 세번째 비트는 MF(more fragment?)
            - 분할된 패킷이 더 있으면 1, 아니면 0
- Fragment Offset
    - 분할된 패킷의 내용이 원래의 분할 전 데이터에서 위치하는 상대 주소 값. 패킷 재조립시 필요
- TTL(Time To Live)
    - 라우터에서 라우터로 갈때 TTL이 1씩 감소
    - 8비트를 차지하므로 0~255. 즉 최대 라우터를 256번 지나면 0됨
    - 0되면 라우터가 패킷을 버림
- Protocol
    - 상위 계층의 프로토콜을 저장 (TCP: 0x06, UDP: 0x11)
- Header checksum
    - 전송간 오류가 있는지 없는지 체크하는 값
- source address
    - 출발지 주소
- Destination address
    - 도착지 주소

### ✢ IPv6 header
-> IPv4의 불필요한 필드를 제거하여 빠른 처리를 가능하게 함

![IPv6 header](https://github.com/devjunmo/TIL/raw/main/img/IP/IPv6_header.png)
- Traffic Class
    - IPv4의 TOS와 유사
- Flow Label
    - 하나의 연속 스트림으로 전송해야 하는 연관 패킷의 전송 기능을 지원함으로써, 실시간 기능이 필요한 멀티미디어 응용 환경을 수용할 수 있다.
- payload length
    - 페이로드 부분의 길이를 나타냄 (~2^16(65536))
- Next header
    - IPv4의 Protocol 같은 역할
- Hop limit
    - IPv4의 TTL과 같은 역할
- checksum 필드 빠짐
    - 헤더의 효율화를 위해 상위 프로토콜에 있는 checksum필드 제외
    - UDP+IPv6의 경우 UDP에 반드시 체크섬 필드 사용해야함