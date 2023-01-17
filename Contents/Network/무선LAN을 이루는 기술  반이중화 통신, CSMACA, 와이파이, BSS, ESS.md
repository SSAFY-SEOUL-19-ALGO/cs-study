# 무선LAN을 이루는 기술 반이중화 통신, CSMACA, 와이파이, BSS, ESS

## 링크 계층

-   유선 혹은 무선 등으로 데이터를 전달하며 장치 간에 신호를 주고받는 규칙을 정하는 계층입니다. 해당 계층은 **물리 계층**과 **데이터 링크 계층**으로 나누어 이야기한다.
-   물리계층 : 무선 LAN과 유선 LAN을 통해 데이터를 보내는 계층
-   데이터 링크계층 : 이더넷 프레임을 통해 에러 확인, 흐름 제어. 접근제어를 담당하는 계층입니다. ( 데이터 링크 계층에서 의 통신은 노드와 노드 사이에 이루어진다)
-   노드 : 연결된 컴퓨터 ( 클라이언트, 서버, 라우터.. 등)
-   링크: 컴퓨터들을 연결하는 연결 매체 ( 유선랜, **무선랜** )

![Image](https://user-images.githubusercontent.com/103018534/212535457-6a30b52e-637a-4ff2-8815-bba7492d2bb1.png)

</br>

## 무선 LAN

무선 LAN은 무선 신호 전달 방식을 이용하여 2대 이상의 장치를 연결하는 기술입니다. 공기 중에 주파수(2.4 GHz, 5 GHz)를 쏘아 무선 통신망을 구축하게 됩니다.

</br>

## 무선 LAN의 통신방식 : 반이중화 통신

-   통신 채널에 접속된 두 대의 단말기 중 어느 한쪽이 데이터를 송신하면 상대편은 수시만 가능한 통신
-   송신측과 수신측이 정해져 있지 않으며 양 단말기의 상호 협력에 의해 송수신 방향 전환
-   하나의 통신 채널을 이용하여 교대로 데이터 송수신

</br>

## CSMA / CA

### _CSMA(carrier sense multiple access)_

: listen before transmit: 전송 전 다른 frame이 전송중인지 확인 후 전송
=> 먼저 전송을 시작했지만, 다른 Host에 도달하기 전까지는 listen을 해도 알 수가 없음
=> 기다리던 두 Host가 동시에 시작하면 충돌이 일어남.
=> 충돌을 완전히 막을 수 없기 때문에 그 충돌로 인한 피해를 최소화 하기 위해 나온 것이 CSMA/CD

</br>

#### CSMA/CD(collision detection)

=> 충돌이 감지되면 모든 host가 frame 전송을 멈춤</br>
=> 대기 random time을 두배씩 늘려가면서 재전송</br>
=> Host가 많을수록 대기 시간이 늘어날 수밖에 없음.

</br>

#### CSMA/CA(collicion avoidance)

_feedback 도입_
무선의 경우, 충돌 감지가 어렵기 때문에 링크 계층에 (이전에 전송 계층에서 본) ACK를 도입함

내 바로 앞에 있는 AP와 나 사이의 feedback(ACK)
=> feedback이 오기 전까지 충돌이 났는지 안났는지 모르기 때문에 실제로 충돌이 일어나도 계속해서 frame을 보낼 것이고 그만큼 시간은 낭비됨. 다른 host와 경쟁적으로 ACK를 받을 때까지 계속해서 재전송이 일어남

=> 이것을 개선하고자 RTS-CTS를 도입

### RTC-CTS

![Image](https://user-images.githubusercontent.com/103018534/212536207-4ffc8fea-60d3-4c20-832e-64eba27378fe.png)
host는 frame을 보내기 전에 작은 RTS를 전송함. 충돌이 일어나면 재전송.
AP는 RTS를 받고 CTS를 broadcast
RTS(A) => CTS(A) \*CTS에는 A가 얼마만큼 사용할거니까 다 조용히 하라는 메시지가 담겨있음
A의 전송이 끝나면 ACK를 feedback
즉, 채널 예약제라고 보면 된다

</br>

### 와이파이 (Wifi)

-   전자기기들이 무선 LAN 신호에 연결할 수 있게 하는 기술
    와이파이를 사용하려면 무선 접속 장치(AP, Access Point)가 있어야 한다. 이를 공유기라고 한다.
-   공유기는 유선 LAN에 흐르는 신호를 무선 LAN 신호로 바꿔주어 신호가 닿는 범위 내에서 무선 인터넷을 사용할 수 있도록 한다.
-   블루투스도 같은 방식이다.

</br>

### BSS ( Basic Service Set) & ESS ( Extended Service Set)

-   AP가 모여서 BSS가 된다.
-   BSS가 모여서 ESS가 된다.
-   base station = access point(AP)
-   BSS(Basic Service Set)
-   host들은 가까이 있는 AP에 요청을 하게 됨
