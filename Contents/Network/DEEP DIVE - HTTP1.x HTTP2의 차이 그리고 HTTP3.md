# DEEP DIVE : HTTP/1.x HTTP/2의 차이 그리고 HTTP/3

## HTTP/1.x

- 기본적으로 연결당 하나의 요청을 처리하도록 설계
- 그로 인해 RTT 증가
- RTT 증가를 해결하기 위해 다양한 기술 사용
    - 이미지스프라이트 : 여러개의 이미지를 하나의 이미지에 합쳐서 하나의 이미지만 다운 받고 bacground-position으로 특정 이미지 표기
    - 코드압축 : 코드에서 들여쓰기, 개행문자, 빈칸 등의 필요없는 부분을 제거하여 용량을 낮춤
    - Base64 인코딩 : 이미지를 html내에 base64 문자열로 첨부할 경우 37%정도의 용량이 증가하지만 서버에 HTTP 요청을 할필요가 없어짐
    - keep-alive 옵션 : 매번 TCP 연결을 새로 하지 않고 한번 연결만으로 여러개의 파일 송수신 가능(HTTP/1.0에서도 존재했지만 HTTP/1.1에서 표준화)

      ![Untitled](https://user-images.githubusercontent.com/47595515/211577985-fa444942-8c08-401c-b020-a446df1b2612.png)
        
- HOL Blocking 문제

  ![Untitled 1](https://user-images.githubusercontent.com/47595515/211577788-9a62b18a-0733-4170-b286-c7c94dfa6578.png)
    
    - 네트워크에서 같은 큐의 첫번째 패킷에 의해 지연될 때 발생하는 성능 저하
    - 위의 이미지에서 image.jpg, styles.css, data.xml은 순차적으로 받아지지만 image.jpg의 다운이 지연될 경우 전체 다운로드가 지연됨

## HTTP/2

- SPDY 프로토콜에서 파생
- HTTP/1.x 보다 지연 시간을 줄이고 응답시간을 더 빠르게 할 수 있음
- `멀티플렉싱`, `헤더 압축`, `서버 푸시`, `스트림 우선순위 설정`을 지원
- HOL Blocking을 해결
- 멀티플렉싱 (****Multiplexed Streams)****
    - 하나의 TCP 연결에 여러개의 스트림을 사용하여 데이터들을 동시에 병렬로 송수신

      ![Untitled 2](https://user-images.githubusercontent.com/47595515/211577794-099c3093-710d-4c24-8adb-cf231ad6fdd9.png)
        
    - 특정 스트림의 패킷이 손실될 경우 다른 스트림에는 영향이 없음
    - 응답 순서에 상관없이 스트림을 주고 받음

      ![Untitled 3](https://user-images.githubusercontent.com/47595515/211577795-8f29a904-bd2c-48da-af4f-f704f2aa1198.png)
        
- 헤더 압축 (****Header Compression)****

  ![Untitled 4](https://user-images.githubusercontent.com/47595515/211577797-66a024da-44ec-43e4-b8ca-db65f1c05d0e.png)
    
    - HTTP/1.x의 크기가 큰 헤더의 문제를 HTTP/2에서는 헤더 압축으로 해결
    - `허프만 코딩` 압축 알고리즘을 사용하는 HPACK 압축 형식을 가짐
    - 허프만 코딩 (Huffman Coding)
        - 문자열을 문자 단위로 쪼개고 빈도수를 센다
        - 빈도가 높은 정보는 적은 비트수를 사용하여 표현
        - 빈도가 낮은 정보는 많은 비트수를 사용하여 표현
        - 전체 데이터의 표현에 필요한 비트양을 줄임
- 서버 푸시 (****Server Push)****
    - 향후 요청에서 예상되는 추가 정보를 미리 클라이언트에 푸시할 수 있음
    - 예) html은 css와 js파일이 포함되기 마련인데 html을 읽으면서 그 안에 참조된 css, js파일을 서버에서 클라이언트로 푸시하여 미리 보낸다

      ![Untitled 5](https://user-images.githubusercontent.com/47595515/211577798-f1345574-88e5-4262-a3be-2927fc52577e.png)
        
- 스트림 우선순위 설정 (****Stream Prioritization)****
    - 클라이언트가 선호하는 응답 수신 방식을 지정해서 응답을 받을 수 있음
    - 예) html문서 내에 css파일 1개와 이미지파일 2개가 존재하고 이를 클라이언트가 요청할 경우
        - css파일의 수신이 이미지파일보다 늦어질 경우 브라우저 렌더링에 문제 발생
        - 이러한 상황을 고려하여 리소스 간의 의존관계에 따른 우선순위 설정 가능

## HTTP/3

- UDP 기반의 QUIC 프로토콜을 사용하여 통신

  ![Untitled 6](https://user-images.githubusercontent.com/47595515/211577801-92eb76ab-8054-4409-96d7-9440ec7d71e4.png)
    
- 멀티플렉싱 지원
- 초기 연결 설정 시 지연 시간 감소

  ![Untitled 7](https://user-images.githubusercontent.com/47595515/211577802-51f99901-f70e-441b-8d0d-44915b2cc340.png)
    
    - QUIC는 UDP 기반이기 때문에 3-Way Handshake 과정을 거치지 않음
    - 첫 연결 설정에 1-RTT 소요
- 순방향 오류 수정 메커니즘(FEC, Forword Error Crrection)
    - 전송한 패킷이 손실되었다면 수신 측에서 에러를 검출하고 수정
    - 열악한 네트워크 환경에서도 낮은 패킷 손실률을 자랑