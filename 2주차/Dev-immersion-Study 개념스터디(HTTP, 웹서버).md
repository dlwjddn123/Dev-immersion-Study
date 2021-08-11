# WEB

## 목차
<br>

## 1. HTTP
## 2. apache, nginx와 Node.js의 차이
## 3. NoSQL과 RDBMS의 종류, 장단점 비교
<br>

---------------------------------------

## 1. HTTP

### HTTP와 HTTPS에 대한 간단한 정의

HTTP(Hyper Text Transfer Protocol) 는 **인터넷에서 데이터를 주고받을 수 있는 프로토콜이다.** <br>
프로토콜이란 데이터를 주고 받기 위한 통신 규칙이라고 보면 되겠다.<br>

그러면 HTTPS는 뭘까? HTTPS는 **Hypertext Transfer Protocol Over Secure Socket Layer** 약자이다.<br>
단어를 보면 알 수 있듯이 HTTP 프로토콜에서 보안 기능(SSL)이 추가된 프로토콜이라고 보면 된다.<br>

### HTTP의 동작 방식 <br>

클라이언트(크롬, 사파리 등의 웹 브라우저, 모바일 등)가 브라우저를 통해서 어떠한 서비스를 **URI** 를 통해서<br>
서버에 요청(request)하면 서버에서는 해당 요청에 대한 결과를 응답(response)하는 형태로 동작한다.<br>
**URI는 Uniform Resource Identifier의 약자로 통합 자원 식별자라는 뜻을 가지고 있고** <br>
**쉽게 말하면 인터넷에 있는 자원을 나타내는 유일한 주소이다**<br>

### HTTP의 요청 메소드
<br>

#### GET 방식
<pre>
<code>
  단어에서 유추 가능하듯이 특정 리소스(자원)을 받기 위한 요청이다. 따라서 리소스를 생성하거나 수정 및 삭제<br>
  등에 사용해서는 안된다.<br>
</code>
</pre>
<br>

#### POST 방식
<pre>
<code>
  주로 리소스를 생성하는데 사용한다. 쉽게 생각하면 우리가 게시판에 글을 작성할 때 사용된다고 볼 수 있겠다.
</code>
</pre>
<br>

#### PUT 방식
<pre>
<code>
  변경 가능한 리소스를 업데이트 하는데 사용한다. 작성한 글을 수정할 때 사용된다고 보면 이해하기 쉽다.
</code>
</pre>
<br>

#### DELETE 방식
<pre>
<code>
  단어에서 유추 가능하듯이 특정 리소스를 제거하는데 사용한다. 글 삭제에 사용.
</code>
</pre>
<br>

#### 이 외에도 HEAD, OPTIONS가 있지만 주로 쓰이는 4가지 방식에 대해서만 설명하겠다.
<br>
<br>


### HTTP/1.1 과 HTTP/2 차이
<br>

<img src="https://miro.medium.com/max/1328/1*rf2AnDQyHfGO_ThYfb-hWA.png">

그림처럼 HTTP1.1은 기본적으로 연결당 하나의 요청과 응답을 처리하기 때문에 동시전송, 다수의 리소스를 <br>
처리하기에 속도와 성능 이슈를 가지고 있다.<br>
**이런 이슈를 해소시켜주는 것이 HTTP2이다.**<br>
HTTP2는**Multiplexed Streams, Stream Prioritization, Server Push, Header Compreestion** 을 사용하여<br>
성능 뿐만 아니라 속도 또한 눈에 띄게 향상 시켰다.<br>
<br>

**Multiplexed Streams : 하나의 연결에서 여러개의 메세지를 동시에 주고 받을 수 있음** <br>
**Stream Prioritization : 요청 리소스간 의존관계를 설정할 수 있음** <br>
**Server Push : HTML문서상에 필요한 리소스를 클라이언트의 요청 없이 보내줄 수 있음** <br>
**Header Compreestion : Header 정보를 HPACK압축방식을 이용하여 전송**<br>

<img src="https://miro.medium.com/max/875/1*m3TqLQ2sXE51-6b8rNLsmA.gif" width=70% height=70% >


