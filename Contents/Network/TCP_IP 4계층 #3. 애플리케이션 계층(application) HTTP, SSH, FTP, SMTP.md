## Application Layer(응용계층)

- 프로토콜 : HTTP, SMTP, SSH, FTP 등
- 웹서비스, 이메일 등 서비스를 실질적으로 사용자에게 제공하는 계층

## HTTP (Hypertext Transfer Protocol)

- 처음에는 서버와 브라우저간에 데이터를 주고 받기 위해 설계된 프로토콜
- 지금은 브라우저 뿐만 아니라 서버와 서버간의 통신할 때도 많이 이용
- 헤더를 통한 확장이 쉬움

  ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b2fd50fa-87d9-4cb8-8832-8397d6d84256/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20221112%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20221112T135252Z&X-Amz-Expires=86400&X-Amz-Signature=4386dd61f7eb9cf198f2695b550b93b4282e42f2fa22a70d0783e7813f0528a7&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

    - 헤더에 쉽게 다른 값들을 추가할 수 있다
- stateless
    - 동일한 연결에서 연속적으로 수행되는 두 요청 사이에 연속적인 상태(state)값은 없다
    - 서버에서는 클라이언트를 기억하지 못한다

  ![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8cfdafe4-50c7-40eb-9f3b-99b09e53be93/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20221112%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20221112T135312Z&X-Amz-Expires=86400&X-Amz-Signature=a2d8e91fd6c2f8ec75a644c62498fcac25eeb0dc8c3194417fb5b278b8737c1a&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)


## SSH (Secure SHell Protocol)

- 보안되지 않은 네트워크에서 네트워크 서비스를 안전하게 운영하기 위한 암호화 네트워크 프로토콜
- 예) AWS EC2에 접근하기 위해 ssh로 프라이빗 키를 이용해 접속

## FTP (File Transfer Protocol)

- 노드와 노드간의 파일을 전송하는데 사용되는 프로토콜
- 지금은 파일을 암호화해서 전송하는 FTPS 또는 SFTP로 대체

## SMTP (Simple Mail Transfer Protocol)

- 인터넷을 통해 메일을 보낼때 사용되는 프로토콜
- 예) Nodemailer라는 JS를 기반으로 SMTP를 통해 메일을 보낼 수 있는 라이브러리

    ```jsx
    // create reusable transporter object using the default SMTP transport
    let transporter = nodemailer.createTransport({
    	host: "smtp.ethereal.email",
    	port: 587,
    	secure: false, // true for 465, false for other ports
    	auth: {
    		user: testAccount.user, // generated ethereal user
    		pass: testAccount.pass, // generated ethereal password
    	},
    });
    ```