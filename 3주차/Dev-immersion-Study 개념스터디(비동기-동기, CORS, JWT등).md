# 목차 <br>


## 1. Javascript의 비동기 기술
## 2. CORS
## 3. JWT
## 4. 테스트 프레임워크
## 5. Dependecy Injection
## 6. Javascript Decorator
## 7. Nest.js
## 8. 데이터베이스 ORM

-------------------------

## 1. Javascript의 비동기 기술

+ ### 블로킹과 논 블로킹
<pre>
<code>
  Blocking 과 Non-Blocking 은, '제어권' 관점에서 접근하는 방식이다.
  Blocking이라는 것은 한국어로 '막혀 있다' 라는 뜻이다.
  즉, 호출된 함수가 제어권을 넘겨주지 않아, 호출한 함수측에서는 다른 작업을 수행할 수 없이 제어권이 돌아오기를 기다리는 것을 말한다.
  그에 반해, Non-Blocking은, 제어권이 넘겨 지지 않으므로, 대상의 작업 처리 여부와 상관이 없이 호출한 함수 측에서 제어권을 가지고 다음 작업들을 수행할 수 있다.
  즉, Non-Blocking 으로 이루어진다는 것은,
  제어권은 호출한 함수 측에서 계속해서 가지고 있기 때문에, 만약에 다른 함수가 실행된다면 그 함수에 대한 결과값을 받을 수 있는 상황인지 체크하는 과정이 필요한 것이다.
  이러한 맥락에서 JS 에서는 이벤트 루프가 돌아가면서 그런 과정을 도맡아 주는 것으로 이해했다.
</pre>
</code>

+ ### 동기와 비동기
<pre>
<code>
  Blocking 은 '제어권' 의 관점으로 바라보았다면, Synchronous, 는 서로 '시간' 관점에서 접근해야 한다.
  설명을 하기 쉽게 호출된 함수와 호출한 함수 두 함수 관점에서 바라보겠다.
  Synchronous 는 두 함수의 시작과 종료 시간에 대해 맞춰져야한다는 뜻이다.
  스택에서 함수 하나가 빠져 나가고, 다음 함수가 실행이 되고, 이런 느낌으로 시간이 지켜지면서 순차적으로 일어날 수 있는 것을 의미한다.
  실제로 한국어로 동기화 또한 그런 맥락에서 들어맞기 때문에 이해하는 데에 도움이 되었다.
  Asynchronous 는 당연히 Synchronous 와 반대로, 두 함수의 시작과 종료 시간이 완전히 맞춰지지가 않는다는 뜻이다.
  호출한 함수는 호출된 함수의 결과를 기다리지만, 제어권이 어떻게 될지는 관심이 없다.
  비동기적으로 다른 함수가 실행이 된다는 데에 의미가 있고 호출된 함수의 결과값을 받게 되는데,
  다른 비동기 함수로부터 받은 결과값에 대해 모든 순서가 완전히 보장이 될 수는 없다는 의미이다. Ajax 가 대표적인 그 예시이다.
</pre>
</code>

+ ### 자바스크립트의 비동기 처리 기술 변화(callback, promise, async-await)

+ ### callback함수 <br>

콜백함수는 말 그대로 나중에 호출되는 함수를 말한다. 일반적인 함수와 같지만,<br>
어떤 이벤트가 발생했거나 특정 시점에 도달했을 때 시스템에서 호출하는 함수이다.<br>
즉, 콜백함수는 콜백함수라는 특별한 문법적 특징을 가진 것이 아닌, **호출방식**에 의한 구분이다.<br>
그런데 이 콜백함수가 계속 중첩되고 쌓이다보면 가독성도 떨어지고 코드 수정하기도 무척 번거러워진다.<br>
이를 콜백 지옥이라고 하며 이를 방지하기 위해 promise와 async-await을 사용한다.

+ ### promise <br>

프로미스 객체는 콜백함수와 하는 역할은 같지만 코드의 가독성을 높혀주고 코드의 흐름을 일관성 있게 해준다.

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FwfABM%2FbtqE75Vbwmi%2FTWsGY601nohorgQOIgE5gk%2Fimg.png">
위 그림과 같이 프로미스는 3가지 상태를 가지고 있는데, <br>
<br>

+ pending(대기) : 비동기 처리 로직이 아직 완료되지 않은 상태
+ fulfiled(이행) : 비동기 처리가 정상적으로 완료되어 프로미스가 결과 값을 반환해준 상태
+ rejected(실패) : 비동기 처리가 실패하거나 오류가 발생한 상태
<br>

``` javascript
  const myPromise = new Promise((resolve, reject) => {
  // 구현..
})
```

프로미스는 객체가 이행상태가 되었을 때.then()메소드로 처리 결과 값을 받을 수 있고 이는 또 다 다른 프로미스 객체가 반환되어<br>
여러번의 프로미스 객체가 연결될 수 있다. (Promise Chaining) <br>

+ ### async & await 

async는 promise의 코드를 더 줄여주고 더 가독성을 높혀준다. <br>
사용법은 function 앞에 async만 붙여주면 되고 비동기로 처리되는 부분 앞에 await를 붙이면 된다. <br>
주의할점은, await 뒤에 오는 부분과 async가 붙은 함수의 반환값은 promise객체를 반환해야 한다는 것이다.

<br>
<br>

#### 사용예시

``` javascript
   async function test(){
    await foo(1, 2000)
    await foo(2, 500).then( () => {
        foo(3, 1000)
    })
}

function foo(num, sec){
    return new Promise(function(resolve, reject){
        setTimeout( function(){
            console.log(num);
            resolve("async는 Promise방식을 사용");
        }, sec);
    });
}
test();
```

---------------------------------

## CORS
<br>

**CORS**는 Cross-Origin-Resource Sharing의 줄임말로 웹개발을 하는사람이라면 한번 쯤은 겪는 에러가 바로 **CORS에러**이다.<br>
브라우저 간의 데이터를 주고받는 과정에서, 도메인 이름이 서로 다른 사이트 간 api요청을 할 때, <br>
공유 설정을 제대로 설정해주지 않았다면 CORS에러가 발생한다. <br>
정확하게 설명하자면 CORS는 우리가 서로 다른 사이트 간 자원에 접근할 수 있는 권한을 부여하도록 하는 정책이고, <br>
위의 에러를 뜨게 하는 것은 **SOP(Same Origin Policy)** 이다. SOP는 우리가 설정하는 것이 아닌 브라우저 단의 보안이다. <br>
<br>

해결방법은 많이 있지만 두 가지만 다뤄보면<br> 
**첫번째는, 서버와 클라이언트 모두 자신이 제어할 수 있는 경우** 에는 서버에서 Access-Control-Allow-Orgin 헤더를 설정해주는 것이다. <br>

``` javascript
  const express = require('express');
  const app = express();
  
  app.get('/api', (req, res)=>{
      res.header("Access-Control-Allow-Origin","허용하고자 하는 도메인");
      res.send(data);
});
```
<br>
위와같이 사용하면 되는데, Access-Control-Allow-Origin:* <= 이런식은 지양하는게 좋다. * 은 모든 도메인을 허용한다는 의미, <br>
때문에 보안상 문제가 될 수 있으므로 왠만하면 사용하지 않아야 한다.<br>

**두번째는, 프록시 서버를 사용해 우회하는 방법이다.** <br>
이를 사용하기위해 우선 터미널에서 npm install http-proxy-middleware 를 입력하고, <br>

```
const { createProxyMiddleware } = require('http-proxy-middleware');

module.exports = function(app) {
  app.use(
    '/api',
    createProxyMiddleware({
      target: 'http://localhost:5000',
      changeOrigin: true,
    })
  );
};
```
위와 같이 작성하면, /api라는 주소로 요청을 보낼 때 localhost:5000으로 바꿔서 요청을 보내게 된다. <br>
결과적으로 클라이언트와 서버는 똑같은 리소스이기 때문에 CORS가 발생하지 않는다. <br>


-------------------------
## JWT <br>

<img src="https://velopert.com/wp-content/uploads/2016/12/jwt-title.png">
<br>
<br>

+ JWT는 Json Web Token 약자로 JSON 객체를 사용해서 토큰 자체에 정보를 저장하는 Web Token 이다. <br>
JWT 정보를 request에 담아 사용자응 정보 열람, 수정 등 개인적인 작업 등을 수행할 수 있게한다. <br>
<br>

<img src="https://media.vlpt.us/images/geunwoobaek/post/88177b57-8888-4759-b4b8-59543a0b026e/image.png">
<br>

위 사진처럼 JWT는 Header, Payload, Signature 이 세가지로 구성된다. <br>

+ #### Header  : 사용한 해쉬 알고리즘 <br> 
#### 서명(ID+Password)에 해당하는 부분을 암호화 시킬 필요가 있는데 해독 알고리즘 정보가 담겨있다. <br>
+ #### Payload : 담을 내용 <br> 
+ #### Signature : 서명(ID+Password) <br>

### JWT의 동작방식 <br>

1. 브라우저의 로그인과정에서 회원정보를 입력(ID,PASSWORD)
2. 서버는 JWT를 만듦
3. 서버는 브라우저에게 JWT를 보냄
4. 브라우저는 JWT를 가지고 서버에게 데이터를 요청
5. 서버는 서명을 확인하고 유저 정보를 클라이언트에게 제공

<img src="https://blog.kakaocdn.net/dn/bARRUx/btqGDQEf5p1/MBoTKadQziR8skS9DqSAxk/img.png"> <br>
<br>
<br>

## 테스트 프레임워크


