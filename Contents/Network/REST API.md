# REST API

## API

**Application Programming interface의 약자**

소프트웨어와 소프트웨어 사이 데이터 전송을 가능하게 하는 프로그램

그중 REST라는 형식을 따르는 API를 **REST API** 라고 한다.
![Image](https://user-images.githubusercontent.com/103018534/212534378-55cf013f-6db4-4f96-8eb8-09d7539bc138.png)

</br>

## REST

**REpresentational State Transfer의 약자**

컴퓨터 시스템간에 상호운용성을 제공하는 방법 중 하나이다.

분산 하이퍼 미디어 시스템(예: 웹)을 위한 아키텍쳐 스타일

</br>

## 등장배경

Q. 팀 버너스리: 어떻게 하면 인터넷에서 정보공유를 잘 할 수 있을까?

A. 이에 대한 해답으로 웹이 탄생했다. 모든 정보를 하이퍼텍스트로 연결한다.

-   정보의 표현형식 : HTML
-   정보의 식별자: URI
-   정보의 전송방법 : HTTP

HTTP가 World Wide Web의 전송 프로토콜로 널리 사용되고 있었고. 웹이 급속도로 성장하고 있었다. Roy T. Fielding이 HTTP설계에 참여하면서 고민이 생겼다. 어떻게 하면 기존의 웹을 망가트리지 않고 HTTP 프로토콜을 향상시킬 수 있을지 고민한다.

⇒ REST의 개념이 등장한다! 웹의 **독립적인 진화**를 위해서

⇒ REST는 기술이나 제품이 아닌 형식이기 때문에 어떤 프로그래밍 언어를 쓰든, 무슨 프레임워크를 쓰든 어떤 소프트웨어를 만들든 이 폼에 맞춰서 정보를 주고 받는다면 독립적으로 진화 할 수 있겠다 생각!! ( 우체국의 송장을 채워넣는 것처럼! )

</br>

## REST를 구성하는 스타일

REST 아키텍쳐 스타일(형식)이고 아키텍쳐 스타일은 제약조건의 집합이다.
따라서 다음과 같은 제약조건을 모두 따라야 REST형식을 따른다고 말 할 수 있다.

![Image](https://user-images.githubusercontent.com/103018534/212534619-9e21d832-c77c-47af-afa3-d355a0fdac5d.png)
오늘날의 HTTP만 잘따라도 REST의 형식을 만족한다!! 한가지 uniform-Interface라는 스타일을 잘 만족하지 못한다.

</br>

## 1. Client-Server

-   클라이언트와 서버가 서로 독립적인 구조를 가진다
-   사용자들에게 제공하는 interface인 User Interface와 데이터 스토리지, 알고리즘 등 서버 내부의 작업들을 분리함으로 써 User Interface는 여러 플랫폼에서의 이식성을 향상될 수 있으며, 서버는 그 구성요소를 단순화하여 확장성을 단순화할 수 있습니다.
-   클라이언트와 서버가 서로 의존하지 않고 별도로 진화할 수 있습니다. 클라이언트는 서버의 리소스 URI만 알고 있으면 되기 때문입니다.

## 2. Stateless

-   **클라이언트에서 서버로의 각 요청에는 그 요청을 이해하는 데 필요한 모든 정보가 포함**되어야 합니다.
-   REST API를 구현하는 서버에서는 session을 이용한 로그인 유지 기능을 구현을 지양해야한다
-   REST API에서는 서버가 session을 가지지 않습니다. 물론 REST API서버에도 session을 추가하여 사용할 수 있지만 이는 REST가 지향하는 바가 아닙니다. 대신 **REST API는 토큰(token) 인증방식**을 사용하게 됩니다.
-   HTTP가 stateless성질을 가지고 있기 때문에 충족이 되지만 session을 사용해서 로그인유지기능을 구현할 경우 stateless한 부분이 stateful하게 변하기 때문에 REST API구현하는 서버에서는 이를 지양하고 있다.

## 3. Cache

-   네트워크 요청시 해당되는 자원들을 복사해서 메모리에 저장해 두었다가 또 같은 요청이 들어왔을 때 네트워크 요청을 하지 않고 브라우저메모리에 있던 자원을 다시 반환한다.
-   이런한 캐싱은 네트워크 요청을 줄여주고 UX 향상에 도움을 준다.
-   캐싱된 데이터가 유효한지 판단하기위해 ‘Last-modified’와 ‘Etag’를 붙여서 확인한다.

## 4. Layered System

-   계층구조로 아키텍쳐를 만들수 있다는 것을 뜻한다.
-   계층화된 시스템 아키텍처를 사용하여 **각 구성들 간의 계층을 마음대로 상호작용 할 수 없도록 제한**
-   독립적인 구조를 가진다, HTTP가 가지는 특성을 통해 만족하게 된다.

## 5. Uniform interface

![Image](https://user-images.githubusercontent.com/103018534/212534792-e4f9dec0-01cd-481c-b57c-b9cc8eb8681e.png)

왜?? 지켜야하는가

-   리소스(자원)들이 각각의 **독립적인 인터페이스**를 가져 웹의 독립적인 진화를 위해서!!!
-   서버와 클라이언트가 각각 독립적으로 진화해서 서버의 기능이 변경되어도 클라이언트를 업데이트 할 필요가 없다!! ( = 웹페이지를 변경해도 웹브라우저의 업데이트 없이 잘 작동한다, HTML 명세가 변경되어도 웹페이지는 잘 작동해야한다.)

> ### 5-3 . Self-descriptive message

> > -   메시지가 스스로를 설명한다.
> > -   HTTP 메시지만으로 어떤 동작이나 정보를 위한 것인지를 메세지 자체로 추론이 가능해야한다.
> > -   HTTP Header에 타입을 명시하고 각 메시지(자원)들은 MIME type에 맞춰서 표현되어야한다.
> > -   예 ) application/json

> ### 5-4. HATEOAS

> > -   애플리케이션의 상태는 하이퍼링크를 통해 전이 되어야한다
> > -   링크를 따라가면서 애플리케이션의 상태가 전이 된다.
> >     ![Image](https://user-images.githubusercontent.com/103018534/212534879-5162e8c4-18b9-4df2-be71-f3bc680c34b3.png)
> > -   하이퍼링크에 따라 다른 페이지를 보여줘야하며 데이터마다 어떤 URL에서 원했는지 명시해주어야 한다.
> > -   그냥 데이터만 주는게 아니라 link라는 프로퍼티 안에 값을 넣어서 어떠한 URI에서 보내줬는지 명시해야한다.

</br>

## REST API URI 규칙

1. 동작은 HTTP 메소드를 사용한다. ( get , post, put, patch )
2. 확장자는 표기하지 말아야한다
3. 동사가 아닌 명사로 표기한다.
4. URI가 계층적인 내용을 담고 있어야한다.
5. 소문자를 사용하고 너무 길경우 ** - ** ( **hyphen bar)** 을 사용한다
6. HTTP 응답 상태코드를 활용한다.
   </br>
   참조 | [Day1, 2-2. 그런 REST API로 괜찮은가](https://www.youtube.com/watch?v=RP_f5dMoHFc)