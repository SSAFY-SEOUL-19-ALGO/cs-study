# 4-way handshake

4 way handshake는  TCP에서 클라이언트와 서버가 서로의 통신을 종료하는 과정입니다.

1. client -> server : 나 연결 그만두고 싶어
2. server -> client : 응 확인햇어. 그래도 보내던 것은 마저 보낼게
3. server -> client : 나 이제 전송 끝났어 연결 끊자!
4. client -> server : 응 알았어

### 과정

***1. `Client ⇒ Server : FIN`* 클라이언트는 TCP 연결을 종료하겠다는 `FIN` 플래그를 전송한다.**

- 서버가 `FIN` 플래그로 응답하기 전까지 연결을 계속 유지한다.
- 클라이언트는 서버의  FIN을 기다리는 FIN_WAIT 1 상태

***2. `Server ⇒ Client : ACK`* 서버는 클라이언트의 요청(`FIN`)을 받고 확인을 알리는 `ACK` 패킷을 보낸다.**

- 서버는 `ACK Number` 필드를 `Sequence Number + 1`로 설정하고`ACK` 플래그 비트를 `1`로 설정한 세그먼트를 클라이언트에게 전송한다.
- 그 후에 자신의 통신이 끝날 때까지 기다린다. (이 상태가 `TIME_WAIT` 상태이다)
    - 서버가 아직 전송할 데이터가 남아있다면 이어서 계속 전송한다.

***3. `Server ⇒ Client : FIN`*데이터를 모두 보내고 통신이 끝나면 서버는 연결이 종료되었다는 의미로 `FIN` 플래그를 클라이언트에게 전송한다.****

***4. `Client ⇒ Server : ACK`*클라이언트는 서버의 응답(`FIN`) 패킷을 확인했다는 의미로 `ACK` 패킷을 보낸다.****

1. 서버는 클라이언트의 `ACK` 패킷을 받은 후 소켓 연결을 CLOSE 한다.
2. 클라이언트는 서버로부터 받지 못한 데이터가 있을 것을 대비하여일정 시간동안 세션을 남겨놓고 잉여 패킷을 기다리는 과정을 거친다. (TIME_WAIT)

![Untitled](https://chlorinated-koi-491.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F6eea51d2-4e1c-4316-8e25-23102ccdb895%2FUntitled.png?table=block&id=ffad53bf-5e27-4867-9388-371405a45745&spaceId=d8ad458c-030c-46f1-9a64-95efc063dd4a&width=2000&userId=&cache=v2)

# 4-way handshake 시 TCP 헤더의 6개 Control Flag

![Untitled](https://chlorinated-koi-491.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fa9380831-1a83-4650-85b5-ca880c956c0b%2FUntitled.png?table=block&id=545209c1-2d95-49ea-9328-db9264fbe338&spaceId=d8ad458c-030c-46f1-9a64-95efc063dd4a&width=2000&userId=&cache=v2)

![Untitled](https://chlorinated-koi-491.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fbf305dd7-43c4-49e1-81a9-cda8a395a687%2FUntitled.png?table=block&id=218c3319-7485-4e5b-a89e-65a39fba78e5&spaceId=d8ad458c-030c-46f1-9a64-95efc063dd4a&width=2000&userId=&cache=v2)

# Q. Timed wait 이 있는 이유?

![Untitled](https://chlorinated-koi-491.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F28f16b87-68eb-4b4d-b3f1-8cf4102fc174%2FUntitled.png?table=block&id=d4d7a0d5-6c67-41b1-b8cc-8107ebb34a50&spaceId=d8ad458c-030c-46f1-9a64-95efc063dd4a&width=2000&userId=&cache=v2)

1. **데이터의 무결성**

    클라이언트는 서버로부터 받지 못한 데이터가 있을 것을 대비

2. **완전한 연결 해제**

    4way-Handshake 과정에서 클라이언트가 아래 그림과 같이 접속 종료 세그먼트를 송신하고 클라이언트는 서버에게 응답 메시지(ACK)와 FIN 신호(세그먼트)를 수신한 뒤 마지막으로 서버에게 ACK를 송신하려 한다. 이때, 송신한 세그먼트가 중간에 소멸되고, 클라이언트의 상태가 CLOSED 되었다고 가정해보면 클라이언트는 계속해서 서버에게 응답 메시지(ACK)를 송신할 것이다. 하지만 포트는 닫혀있으므로 송신을 할 수 없게 된다. 그리고 서버는 접속 종료를 요청한 클라이언트의 응답 메시지만 계속해서 기다릴 뿐이다.
TIME-WAIT 상태가 존재한다면 클라이언트가 세그먼트를 송신할 때 문제가 발생하면 TIME-WAIT 상태인동안에 포트를 계속 사용중이므로 세그먼트를 재송신을 할 수 있게된다. 재송신한 세그먼트를 수신한 서버는 정상적으로 CLOSED 상태가 되어 접속 종료 요청을 처리할 수 있게 된다.

- 2배의 최대 세그먼트 ( MSL) * 2시간을 기다리게 됩니다.