# 3-way HandShake
연결하고자 하는 두 장치(클라이언트, 서버) 간의 논리적 접속을 성립하기 위해 사용하는 연결 확인 방식

![](https://devkly.com/static/f7691492fbc5d93e57f0d1a59bb28ae1/dd45a/3way-handshake.png)
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FH4UNn%2FbtrHrM0X1FV%2FlXqZKO33gbzEV1krQA9SE1%2Fimg.png)

1. 클라이언트가 서버에 연결 요청 (SYN 단계)
   - SYN Flag = 1
   - Sequenct Number에 시퀀스 번호 a(ISN : 임의의 랜덤 숫자) 함께 전송
2. 서버가 연결 허락 (SYN+ACK 단계)
   - SYN Flag = 1, ACK Flag = 1
   - Acknowledgment Number(a + 1), Sequenct Number(다른 ISN b) 전송
3. 클라이언트와 서버 연결 설정 (ACK 단계)
   - ACK Flag = 1
   - Acknowledgment Number(b + 1) 전송
   - max segment size 중 더 작은 값이 데이터 전송 시 사용된다.
 > ISN : TCP 기반 데이터 통신에서 각각의 새 연결에 할당된 고유한 32비트 시퀀스 번호를 나타낸다. TCP 연결을 통해 전송되는 다른 데이터
  바이트와 충돌하지 않는 시퀀스 번호를 할당하는 데 도움이 된다.