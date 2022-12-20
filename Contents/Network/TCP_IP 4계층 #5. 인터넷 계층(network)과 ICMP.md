## Internet Layer(인터넷 계층)

- 프로토콜 : IP, ICMP, ARP 등
- 한 노드에서 다른 노드로 전송 계층에서 받은 세그먼트 또는 데이터그램을 패킷화하여 목적지로 전송하는 계층

## ICMP (Internet Control Message Protocol)

![Untitled](https://user-images.githubusercontent.com/47595515/207835258-d1e72081-605b-409e-9671-af3305cc7766.png)

- 노드와 노드 사이에서 통신이 잘되나를 확인할때 쓰는 프로토콜
- 데이터 교환에 사용되지 않는 프로토콜
- 호스트가 없거나, 해당 포트에 대기중인 서버 프로그램이 없는 등의 에러 상황이 발생할 경우 IP헤더에 기록되어 있는 출발지 호스트로 이러한 에러에 대한 상황을 보내주는 역할을 수행
- 대표적인 에러메시지
    - Destination Unreachable : 목적지에 도달하지 못함
    - Time Exceeded : 시간이 오래 걸려 목적지에 도달하지 못함
- 일반적으로 테스팅에 사용
- IP와 달리 TCP 또는 UDP와 같은 전송 계층 프로토콜과 연관되지 않고 독립적인 비연결형 프로토콜
- 예) ping, PMTUD 과정에서의 ICMP에러메시지