# IP주소체계 #5. 공인IP(public IP)와 사설IP(private IP)와 NAT

## NAT(Network Address Translation)

![Untitled](https://user-images.githubusercontent.com/47595515/211578915-274ae7fc-c6ad-4f06-a152-af3836bb500a.png)

- IP주소의 부족을 해결하기 위해 공인IP와 사설IP로 나누고 중간에 NAT라는 기술을 사용
- IP주소를 다른 IP주소로 매핑하는 방법
- 패킷이 트래픽 라우팅 장치를 통해 전송되는 동안 패킷의 IP주소를 변경
- NAT을 통해 내부 네트워크 IP가 노출되지 않음
- 실생활에서 공유기가 NAT 라우터 역할을 함