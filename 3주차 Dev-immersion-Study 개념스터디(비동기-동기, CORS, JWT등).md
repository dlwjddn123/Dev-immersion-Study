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

-------------------

## 테스트 프레임워크 <br>

**테스트 프레임워크**는 우리가 짠 코드가 제대로 동작하는 지 확인하기 위해 테스트 케이스를 만들어주는 프레임워크다. <br>

테스트의 종류는  <br>
+ 유닛테스트 : 애플리케이션의 개별 모듈을 독립적으로 테스트-> 보통 메서드 단위의 테스트
+ E2E 테스트 :  해당 시스템과 해당 시스템을 구축하고 배포하는 프로세스를 모두 시험하는 것을 말함 
+ 통합테스트 : 모듈을 통합하는 과정에서 모듈 간 호환성의 문제를 찾아내기 위해 수행되는 테스트 <br>

이렇게 3가지로 구성되고, 그 중에서도 **유닛 테스트**를 작성하는데 집중하는 것이 필요하다.

### Jest

<img src="https://media.vlpt.us/images/seongkyun/post/89f3edd8-c776-47c6-97cb-c616a2bb3f40/1_Q26gw-kNzOXUqZKRr04T-g.png">
<br>

Jest는 자바스크립트 코드의 테스트를 도와주는 모듈이라고 생각하면 되겠다. <br>
**특징으로는 Jest의 가장 큰 장점은 쉬운 설치 및 사용 방법이라 할 수 있다.
Jest는 테스트 러너의 기능뿐 아니라, 단언, 테스트 더블, 코드 커버리지 등 테스트에 필요한 모든 기능을 지원하기 때문에 별다른 추가 설치가 필요 없다.** <br>

간단한 사용예시는 expect()와 toBe()를 사용

``` javascript
test("1 is 1", () => {
  expect(1).toBe(1);
});
```

이렇게 expect안의 값이 toBe안의 값이 된다면(같다면) 테스트는 성공이고 아니라면 실패다. <br>
이외에도 beforeEach, afterEach ,toEqual, describe, it 등 여러가지 사용할 수 있는것들이 있다. <br>

--------------------------
## Dependency Injection(DI) <br>

**Dependency Injection**이란? 해석하면 **의존성 주입**이라는 뜻을 가지고 있다. <br>
의존성 주입 설명에 앞서 여기서 말하는 **의존성**은 OOP(객체지향프로그래밍)에서 클래스간에 의존 관게가 있다는 것을 말하는데, <br>
클래스 간에 의존관계가 있다는 것은 **한 클래스가 바뀔 때 다른 클래스가 영향을 받는것**을 의미한다. <br>

그래서 의존성 주입이란? 클래스간 의존성을 클래스 외부에서 주입하는 것을 뜻한다. <br>
더 자세하게는 **클래스에 대한 의존성의 인터페이스화를 통한 코드 유연성 증대 + 클래스의 인스턴스를 외부에서 생성하여 주입**을 뜻한다. <br>

이것이 필요한 이유는 클래스에서 어떤 한 메소드(예시)가 바뀌면 그 의존성을 가지고 있던 메소드에 모두 영향을 끼치게 되는데, <br>
이때 의존성을 가지고 있던 코드를 전부 수정해줘야 하는 번거로운 일이 생긴다. 따라서 우리는 인터페이스, 혹은 클래스 외부에서<br>
객체를 생성하여 해당객체를 클래스 내부에 주입해줘야 이런 문제를 방지할 수 있다. <br>

<img src ="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbWWKoP%2Fbtq1aRug7wa%2FW7AblITwYgfSvJzA7Yjv31%2Fimg.png"> <br>

위 이미지 처럼 외부에서 객체를 가져오면 코드를 전부 수정할 필요 없이 외부 container(객체를 저장하는 공간)만 수정하면 된다. <br>
이렇게 되면 객체에 대한 제어 권한을 container가 가지게 되는데 이를 IOC(Inversion of Control)제어의 역전 이라고 부른다. <br>

#### DI의 장점
+ 클래스간의 결합도가 약해져, 리펙토링이 쉬워진다.
+ 클래스간의 결합도가 약해져 특정 클래스를 테스트하기 편해진다.
+ 인터페이스 기반 설계는 코드를 유연하게 하고 확장을 쉽게 한다.
<br>

-----------------------------------------
## Decorator
<br>
Decorator(장식자)는 하나의 코드를 다른 코드로 감싸거나, 함수를 감싸는 방법이다. <br>
Decorator는 동일한 클래스의 다른 객체의 동작에 영향을 주지 않고, 정적, 동적으로 개별 객체에 동작을 추가할 수 있다. <br>
기본 기능을 수정하지 않고 기능을 향상시키는데 사용된다.

```javascript
function work() {
  console.log('Some work...');
}
function helloWrapper(wrapped) {
  return function(...args) {
    else {
      console.log('Hello!');
      wrapped.apply(this, args);
    }
  }
}

const wrapped = helloWrapper(work);
```

#### 사용 예시
``` javascript
work();
// Some work...

wrapped();
// Hello!
// Some work...
```
#### 결과
<br>

#### 데코레이터를 사용하는 이유
+ Higher-order function보다 적용하기 쉽다. 특히, Class나 Class member들에 적용할 때는 훨씬 편하다.
+ 읽기 쉽고 코드를 더 깔끔하게 할 수 있다. <br>



----------------------------

## Nest.js
<br>
<img src="https://cdn.inflearn.com/public/courses/327273/cover/77c59c6c-7f86-4d04-ad98-5593defbf6a6/Subscribe%20for%20more%E1%84%8B%E1%85%B4%20%E1%84%89%E1%85%A1%E1%84%87%E1%85%A9%E1%86%AB%20(3).png">
<br>

### Nest.js란? <br>
공식 사이트의 설명을 빌려오자면 <br>
<pre>
<code>  
A progressive Node.js framework for building efficient, reliable and scalable server-side applications. <br>
효율적이고 안정적이며 확장 가능한 서버 측 애플리케이션을 구축하기 위한 진보적인 Node.js 프레임워크입니다. <br>
</pre>
</code>
<br>

**의미있게 봐야하는 문장은 효율적이고 안정적 이라는 문장이다.** <br>

우리는 이 전에 express.js로 웹을 구현한 적이 있다. express.js도 크게 불편함을 느끼진 못했지만 그 이유는 <br>
우리가 아직 대규모 프로젝트를 안해봤고 express는 자유도가 높기 때문에 개발자마다 사용하는 기술, 미들웨어 등이 다를 수 있다. <br>
이는 프로젝트의 통일성을 해치게 되고 그에 따른 수많은 문제가 발생할 수 있다는 말이다. <br>

Nest.js는 이런 문제를 개선해주는데 controller, service, module의 구조와 특정한 패턴을 가지고 있다. <br>
이 구조와 패턴들은 코드를 안정적이고 통일성 있게 해주므로 거대한 프로젝트를 만들기 좋다는 장점을 가진다. <br>

**Express => 가볍고 간편하고 빠르게 간단한 웹을 위한 서버를 만들기 좋다** <br>
**Nest => 통일성 있고 거대한 프로젝트를 만들기 좋다 (자바스크립트계의 스프링이라고도 불림)** <br>

Nestjs를 이번에 사용해보면서 느끼는 점은 틀이 잡혀있어서 좋고 어떻게 써야하는 지 빨리 배우고 싶었지만 <br>
아직 널리 쓰이고 있진 않기 때문에 혼자 배우기가 좀 어려운 부분이 있다.(스프링처럼 널리쓰이는 날이 오기를..) <br>
<br>
<br>

-------------------------------------------------
## 데이터베이스 ORM 

<br>

**ORM(Object-relational Mapping)** 이란 OOP 간의 호환되지 않는 데이터를 변환하는 프로그래밍 기법으로 쉽게 말해 객체로 관계형 데이터베이스를 관리하는 기술이다.<br>
대부분의 개발 언어 platform마다 제공되고 있으며, 대표적으로 spring에는 JPA가, node의 sequalize, 또 Django에는 orm이 내장되어있다. <br>

<br>


+ 기존 SQL 방식의 문제점 <br>

<br>

기존의 SQL로 데이터베이스를 관리하던 때의 문제점은 계속되는 반복되는 코드의 문제점이 있었고,<br>
SQL을 확인하기 전까지는 Entity를 신뢰할 수 없다는 불편함이 있었다.<br>
또한 SQL의 의존적인 개발을 피할 수 없고, 계층 분할의 어려움이 있었다.<br>

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbbm0c4%2FbtqAt7X6ism%2FSTaECebTshwAD1FiI01FAK%2Fimg.png">

<br>

+ ORM을 사용 했을 때 장점  <br>

객체 관계 매핑(Object-relational Mapping)이란 말에 어울리게 ORM을 사용하면 객체는 객체대로 설계하고,<br>
관계형 데이터베이스는 데이터베이스대로 설계하고 중간에서 ORM 프레임워크가 중간에서 매핑을 해주어서로 의존성을 배제할 수 있다.<br>
이를 통해 생산성과 유지보수 성에서 높은 이득을 얻을 수 있다.<br>

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F8GQk1%2FbtqAuMMJKz2%2Fo0QP6sOkvfxmbHUNHLwFj1%2Fimg.png">



