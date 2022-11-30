## IP Address

- IP주소는 네트워크주소와 호스트주소 두 부분으로 나뉨
- 네트워크 주소 :  호스트들을 모은 네트워크를 지칭
    - 네트워크 주소가 동일 = 로컬네트워크
- 호스트 주소 : 호스트를 구분하기 위한 주소
    - 네트워크 호스트는 컴퓨터 네트워크에 연결된 컴퓨터나 기타 장치

## Classful IP Addressing

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fdee7268a-1c5a-4a40-838f-148b204899ac%2FUntitled.png?table=block&id=e9ff1234-1190-4286-835f-ed33f3e269bd&spaceId=3b8cf84b-872f-43de-8148-b0a9d9a8d4a4&width=2000&userId=d9446ff9-ed54-4396-8397-0db52fa23e2d&cache=v2)

![Untitled](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F4261093c-a486-4f3d-9c6d-a12542e8f099%2FUntitled.png?table=block&id=605d5637-7b84-4ffe-a1dc-ac962e39511c&spaceId=3b8cf84b-872f-43de-8148-b0a9d9a8d4a4&width=2000&userId=d9446ff9-ed54-4396-8397-0db52fa23e2d&cache=v2)

- 네트워크 주소를 매기고 그에 따라 네트워크 크기를 다르게 구분하여 클래스를 할당하는 주소체계
- 구분하는 기준자를 서브넷마스크라고 함
- Class D는 멀티캐스트로 사용하는 클래스
- Class E는 연구용으로 사용하는 클래스

### Class A

![Untitled](https://sadoruin-notes.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F6704ef6a-b9ec-418e-a97d-da68de5259f6%2FUntitled.png?table=block&id=63339ba6-f91d-4dc7-ae58-78afbc889a3b&spaceId=3b8cf84b-872f-43de-8148-b0a9d9a8d4a4&width=2000&userId=&cache=v2)

- 2²⁴-2 :  한 네트워크당 16,777,214 호스트 ID (약 1600만개)
- 네트워크 주소 범위 : 1 ~ 126로 시작
    - 127.X는 루프백 주소이기 때문에 포함 x (localhost)
    - 0.0.0.0도 특수주소로 포함 x (알수 없는 대상에 달아 놓는 임시 주소)

### Class B

![Untitled](https://sadoruin-notes.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ffa126634-2493-4d1f-8f4d-45687f660a2a%2FUntitled.png?table=block&id=a870bd21-e378-4e1f-9e8d-9c32f4909f75&spaceId=3b8cf84b-872f-43de-8148-b0a9d9a8d4a4&width=2000&userId=&cache=v2)

- 2¹⁶-2 : 한 네트워크당 65534 호스트 ID (6만 5천개)
- 네트워크 주소 범위 : 128 ~ 191로 시작

### Class C

![Untitled](https://sadoruin-notes.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F1dec54cd-e746-4d50-ae58-1b082808588d%2FUntitled.png?table=block&id=c62c03a8-1587-4b5f-ae3b-f1b66e143ff2&spaceId=3b8cf84b-872f-43de-8148-b0a9d9a8d4a4&width=2000&userId=&cache=v2)

- 2⁸-2 : 한 네트워크당 254 호스트 ID
- 네트워크 주소 범위 : 192 ~ 223로 시작


> 💡 **호스트ID 개수에서 2개를 빼는 이유**
>- 맨 앞자리는 네트워크 주소로 남겨둔다 (XXX.XXX.XXX.0)
>- 마지막 주소는 브로드캐스팅 주소로 남겨놓는다 (XXX.XXX.XXX.255)

## 문제점

![Untitled](https://sadoruin-notes.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F81b6e854-3e89-4389-a422-f122cd612d25%2FUntitled.png?table=block&id=433afb77-9c05-40f6-b8c5-f83ce4c5567f&spaceId=3b8cf84b-872f-43de-8148-b0a9d9a8d4a4&width=2000&userId=&cache=v2)

- 네트워크의 크기가 작은 경우 큰 네트워크를 필요로 하는 조직은 여러개를 확보해야 하는 어려움
    - 5000개의 호스트 주소를 할당받기 위해 여러개의 Class C 네트워크 확보
- 작은 네트워크가 필요한 조직의 경우 너무 많은 IP를 가져가므로 IP가 낭비
    - 5000개의 호스트 주소를 할당받기 위해 Class B를 사용할 경우 사용되지 않는 6만여개의 IP 주소가 낭비