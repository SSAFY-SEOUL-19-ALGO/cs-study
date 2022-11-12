## Internet Layer(인터넷 계층)

- 프로토콜 : IP, ICMP, ARP 등
- 한 노드에서 다른 노드로 전송 계층에서 받은 세그먼트 또는 데이터그램을 패킷화하여 목적지로 전송하는 계층

## ICMP (Internet Control Message Protocol)

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c0e24bb3-5e07-48de-a08d-d1f98da74c9f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20221112%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20221112T134559Z&X-Amz-Expires=86400&X-Amz-Signature=fe98461163c3bef822cb64a988c1512d979afb21cf1333b4887e1f2a5e6cd784&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

- 노드와 노드 사이에서 통신이 잘되나를 확인할때 쓰는 프로토콜
- 데이터 교환에 사용되지 않는 프로토콜
- 호스트가 없거나, 해당 포트에 대기중인 서버 프로그램이 없는 등의 에러 상황이 발생할 경우 IP헤더에 기록되어 있는 출발지 호스트로 이러한 에러에 대한 상황을 보내주는 역할을 수행
- 대표적인 에러메시지
    - Destination Unreachable : 목적지에 도달하지 못함
    - Time Exceeded : 시간이 오래 걸려 목적지에 도달하지 못함
- 일반적으로 테스팅에 사용
- IP와 달리 TCP 또는 UDP와 같은 전송 계층 프로토콜과 연관되지 않고 독립적인 비연결형 프로토콜
- 예) ping, PMTUD 과정에서의 ICMP에러메시지