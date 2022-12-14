# HTTP 상태코드와 메서드(GET, POST, PATCH, DELETE)

유형: 네트워크

## HTTP 상태코드

-HTTP는 페이지의 상태에 따라 상태코드를 제공한다. 세자리 숫자로 구성되며, 첫번째 자리의 숫자를 기준으로 클래스를 나눠 상태를 표현한다.

-1~3은 정상적인 응답코드이지만 4,5일 경우 클라이언트나 서버측에서 오류가 발생한 경우로 사이트 관리자에게 즉시 알려야한다.

![image](https://user-images.githubusercontent.com/102861657/210595509-29f0a278-f359-4e5c-ba30-d6ff76bab37c.png)

HTTP의 상태코드

## HTTP 메서드

-클라이언트가 웹서버에게 사용자 요청의 목적이나 종류를 알리는 수단.

-종류는 총 9가지가 있고, 그 중 5개의 메서드가 주로 사용된다.

- GET : 리소스를 읽기. 성공 시 200, 실패시 404 NOT FOUND 또는 400 코드 반환
- POST : : 리소스를 생성(create), 요청 데이터 처리, 주로 데이터 등록에 사용
- PUT : 자원: 리소스를 업데이트(전체 자원), 요청을 보낼 때 전체를 보내야 함. 해당 리소스가 없으면 생성
- PATCH : 리소스를 일부만 변경, 요청을 보낼 때 수정할 부분을 보내야 함.
- DELETE : 리소스를 삭제

-나머지 메서드 4가지

- HEAD: GET과 동일하지만 메시지 부분을 제외하고, 상태 줄과 헤더만 반환
- OPTIONS: 대상 리소스에 대한 통신 가능 옵션을 설명(주로 CORS에서 사용)
- CONNECT: 대상 자원으로 식별되는 서버에 대한 터널을 설정
- TRACE: 대상 리소스에 대한 경로를 따라 메시지 루프백 테스트를 수행
