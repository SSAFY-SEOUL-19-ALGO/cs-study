## IP 주소

-IP 주소는 논리적 주소(연결에 따라 변하는 주소) 컴퓨터 네트워크에서 장치들이 서로를 인식하고 통신하지 위해 사용하는 특수한 번호.

## MAC 주소

-MAC 주소는 물리적 주소(장치에 설정된 고유 식별 주소) 네트워크 인터페이스에 할당된 고유 식별자이며 보통 장치의 NIC(Network Inteface Card / ex) LAN카드)에 할당된다.

-48 비트로 구성되며, 24비트 OUI와 24비트 UAA로 이루어진다.

- OUI : IEEE에서 할당한 제조사 코드
- UAAA : 제조사에서 구별되는 코드

![](https://charm-ocelot-88c.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F3df1398e-ae8b-4546-8ad7-6d0d7d338c28%2FUntitled.png?table=block&amp;id=848edabb-eba8-4508-aafd-9deb38573e98&amp;spaceId=57052b57-d9fa-41a5-9c4b-f202a3ecf77b&amp;width=1920&amp;userId=&amp;cache=v2)
ipconfig/all을 통해 확인한 내 컴퓨터의 MAC 주소, 앞 C0-B8-83이 OUI, E1-28-FA가 UAAA 코드이다.

-MAC주소는 일반적으로 유일하지만 유일하지 않은 경우도 있다. 제조사의 실수나 또는 의도적으로 UAAA를 중복되도록 할당할수도 있다.(why..?)

-MAC주소를 변경할 수는 있으나 하지 않는것을 권장하며 변경 자체를 어렵게 만든 OS도 있다.

## ARP(Address Resolution Protocol)

-IP주소를 이용해 MAC 주소를 파악하는데 사용되는 프로토콜. 반대로 MAC 주소를 통해 IP 주소를 파악하는 프로토콜을 **RARP(Reverse Address Resolution Protocol)** 라 부른다.