# TCP/IP 4계층 모델

- 인터넷 프로토콜 스위트(Internet Protocol Suite)는 인터넷에서 데이터를 주고 받을 때 쓰이는 프로토콜의 집합 ⇒ TCP/IP4계층이나 [OSI7계층](https://www.notion.so/OSI-7-e125cf31762c4115a4ac16d49936fadf)으로 설명
- TCP/IP: Transmission Control Protocol/Internet Protocol→ 네트워크에서 사용되는 통신 프로토콜의 집합으로 계층들은 프로토콜의 네트워킹 범위에 따라 4개의 추상화 계층으로 구성된다.

## 계층구조

![Untitled](https://telling-starburst-b5b.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F2ac67789-8407-4545-bd9f-04a964704d6b%2FUntitled.png?table=block&id=aebb4f0a-96e2-4e62-8e98-46bb266dec2c&spaceId=728ce3e0-7b4e-47d4-8b23-cbdcc5d949b1&width=2000&userId=&cache=v2)

- 특정 계층이 변경되었을 때, 다른 계층이 영향을 받지 않도록 설계되어 있어 독립적이다.

### Application계층

- 응용 프로그램이 사용되는 프로토콜 계층으로, 서비스를 실질적으로 사람들에게 제공하는 층이다.

<table>
  <tr>
    <td>FTP</td>
    <td>장치와 장치 간의 파일을 전송하는데 사용되는 표준 통신 프로토콜</td>
  </tr>
  <tr>
    <td>SSH</td>
    <td>보안되지 않은 네트워크에서 네트워크 서비스를 안전하게 운영하기 위한 암호화 네트워크 프로토콜</td>
  </tr>
  <tr>
    <td>HTTP</td>
    <td>World Wide Web을 위한 이터 통신의 기초이자 웹 사이트를 이용하는데 쓰는 프로토콜</td>
  </tr>
  <tr>
    <td>SMTP</td>
    <td>전자 메일 전송을 위한 인터넷 표준 통신 프로토콜</td>
  </tr>
  <tr>
    <td>DNS</td>
    <td>도메인 이름과 IP주소를 매핑해주는 서버.<br> 예를 들어 www.naver.com에 DNS쿼리가 오면 [Root DNS]→[com.DNS]→[naver.DNS]→[www.DNS]과정을 거쳐 완벽한 주소를 찾아 IP주소를 매핑한다. 이를 통해 IP주소가 바뀌어도 사용자들에게 똑같은 도메인 주소로 서비스할 수 있다.</td>
  </tr>
</table>

### Transport(전송)계층

- 송신자와 수신자를 연결하는 통신서비스를 제공.
- 연결지향 데이터 스트림 지원, 신뢰성, 흐름 제어를 제공.
- 애플리케이션과 인터넷 계층 사이의 데이터가 전달 될 때 중계역할 수행
- 대표적으로 [tcp](https://www.notion.so/TCP-8d55d7a7ea7a4f9a8c9f4aae1a8d06cc)/[udp](https://www.notion.so/UDP-cf79f95d404249f5801df07d7e7bded5)
    - TCP
        - 연결 지향 프로토콜로, 수신 여부를 확인하여 신뢰성을 구축한다.
        - 가상 회선 패킷 교환 방식: 각 패킷에 가상 회선 식벽자가 포함되어, 모든 패킷을 전송하면 가상 회선이 해제되고, 패킷들은 전송된 순서대로 도착한다.
        - [3-WAY HANDSHAKE/ 4-WAY HANDSHAKE](https://www.notion.so/3-way-handshake-4-way-handshake-f1bc6738c6d94c248647772e61e1cc85)
    - UDP
        - 수신여부를 확인하지 않고, 순서 역시 보장하지 않는다. 단순히 데이터만 보내기 때문에 속도가 빠르다.
        - 데이터그램 패킷 교환 방식: 패킷이 독립적으로 최적의 경로를 선택하여 이동한다. 여러 패킷이 각각의 경로를 선택하기 때문에 순서가 보장되지 않는다.

### Internet(인터넷) 계층

- 장치로부터 받은 네트워크 패킷을 ip주소로 지정된 목적지로 전송하기 위해 사용되는 계층
- 패킷을 수신해야 할 상대의 주소를 지장하여 데이터를 전달한다.
- OSI7계층에서는 물리계층(LAN을 사용하여 0과 1로 이루어진 데이터를 보내는 계층)과 데이터링크계층(이더넷 프레임을 통해 에러확인, 흐름제어, 접근제어를 담당하는 계층)으로 나누어진다.
- 데이터가 제대로 전송되었는지 확인하지 않는 비 연결형
- IP, ARP, ICMP
- 전선, 광섬유, 무선 등으로 실질적으로 데이터를 전달

### Link(링크)계층

- 네트워크 접근 계층이라고도 불림

# 캡슐화/비캡슐화

### 계층 간 데이터 송수신 과정

- 계층 간 데이터 송수신 과정: 애플리케이션 계층에서부터 링크계층까지 요청값이 캡슐화 과정을 거쳐 전달→ 상대의 링크 계층을 통해 해당 서버와 통신→링크 계층으로부터 애플리케이션 계층까지 비 캡슐화 과정을 거쳐 전송
    
    ![Untitled](https://telling-starburst-b5b.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ffa7960e5-9c5e-4de0-b1c9-b84490aca31e%2FUntitled.png?table=block&id=e79d34f7-fb62-43b9-8cbd-1114123de8d4&spaceId=728ce3e0-7b4e-47d4-8b23-cbdcc5d949b1&width=2000&userId=&cache=v2)
    

### 캡슐화 과정

- 상위 계층의 헤더와 데이터를 하위 계층의 데이터 부분에 포함시키고, 해당 계층의 헤더를 삽입하는 과정
- 애플리케이션 계층의 데이터가 전송 계층으로 전달되면서 ‘세그먼트’ 또는 ‘데이터그램’화 되며 TCP(L4) 헤더가 붙여지게된다.

![Untitled.png](https://telling-starburst-b5b.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0190517c-cbfe-4179-9656-47387bad9c21%2FUntitled.png?table=block&id=9f51fac2-66de-4da8-a2af-822359e5e528&spaceId=728ce3e0-7b4e-47d4-8b23-cbdcc5d949b1&width=2000&userId=&cache=v2)

### 비캡슐화 과정

- 하위 계층에서 상위 계층으로 가며 각 계층의 헤더 부분을 제거하는 과정
- 캡슐화된 데이터를 받게 되면 링크 계층에서부터 타고 올라가면서 최종적으로 사용자에게 메시지(애플리케이션의 PDU)로 전달된다.

![Untitled](https://telling-starburst-b5b.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ff44f42a8-3d01-46dc-907e-193789c3d0cc%2FUntitled.png?table=block&id=e50839b2-767a-4f4a-9e05-09fc7990986a&spaceId=728ce3e0-7b4e-47d4-8b23-cbdcc5d949b1&width=2000&userId=&cache=v2)

## PDU(Protocol Data Unit)

- 네트워크의 어떤 계층에서 계층으로 데이터가 전달될 때 한 덩어리의 단위
- PDU는 제어 관련 정보들이 포함된 ‘헤더’, 데이터를 의미하는 ‘페이로드’로 구성되어 있으며, 계층마다 부르는 명칭이 다르다.
- 메시지 - 세그먼트(TCP)/데이터그램(UDP) - 패킷 - 프레임(데이터링크)/비트(물리계층)
    - 패킷 : SP와 DP가 포함된 IP헤더가 붙은 형태의 조각
    - 프레임: MAC주소헤더+CRC/체크섬트레일러
        - crc/체크섬트레일러: 데이터의 오류 감지를 위한 수학적 함수가 적용된 값. 링크의 오류로 인한 데이터 손상을 감지하는 역할을 한다.
- PDU중 가장 아래 계층인 비트로 송수신 하는 것이 가장 빠르고 효율성이 높다.
- 문자열 기반 송수신을 하면 헤더에 AUTHORIZATION값 등 다른 값들을 넣는 확장이 쉽기 때문에, 애플리케이션 계층에서는 문자열을 기반으로 송수신을 한다.