# VSCode Plugins<br>
<br>
<br>



## 1. ESLint
## 2. Prettier
## 3. ESLint와 Prettier의 차이
<br>
<br>

--------------------------------
# 1-1. ESLint란?

먼저 ES와 Lint를 구분해서 뜻을 알아보면<br>
**ES는 ECMA Scrip의 줄임말이고, ECMA Script란 쉽게 말해 표준화된 자바스크립트 언어이다.**<br>
ES6를 들어본 적이 있을텐데 ES6에서 ES가 바로 이 뜻이다.<br>
**Lint는 소스 코드를 분석하여 프로그램의 오류나 버그, 스타일 오류, 의심스러운 구조체에 표시(flag)를 달아놓기 위한 도구들을 가르킨다.**<br><br>
<br>
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FBIU5I%2FbtqGUddQdd2%2F2MzydKzyc7dBp3CmQEWZJK%2Fimg.png">
<br>
<br>
**즉,** 위 사진처럼 오류가 있는 코드를 작성했을 때 빨간 줄이 그이거나 표시가 뜨는 것을 말한다.
<br>
**(위 두 단어를 조합해보면 ESLint는 자바스크립트 언어의 소스코드를 분석해주는 도구임을 알 수 있다)**
<br>

# 1-2 ESLint 사용법
<br>

우선, VS Code의 터미널 기능을 사용해 package.json을 생성해야 한다.

### package.json 생성하기
<br>
터미널에 아래 명령어를 입력하면 package.json을 생성할 수 있다.<br>

=> **npm init -y**    (여기서 -y옵션은 대화형 프로세스를 생략하는 옵션이다. yes의 y이다) <br>

### ESLint 패키지 설치하기<br>

작업을 진행할 디렉토리에 아래 명령어를 입력하자.<br>

=> **npm install eslint** <br>

위 명령어를 실행하면, node_modules라는 폴더가 생성되고 package.json파일에 Dependencies속성에 eslint가 버전과 함께 추가된다.

### .eslintrc 파일을 생성하고 설정 추가하기 <br>

.eslintrc 파일을 package.json 과 동일한 디렉토리에 생성하고 기본적인 설정을 하자.



**{ "extends": "eslint:recommended", <br>
　"rules": { "semi": ["error", "always"], <br>
　　　　　"quotes": ["error", "double"] <br>
　　} <br>
  } <br>**
  
 **1) "extends":"eslint:recommended" <br>**
  코드에서 유추할 수 있듯이 ESLint에서 권장되어지는, rules page에서 체크되어 있는 항목을 자동으로 검사하는 옵션이다. <br>
  
**2) "semi": ["error", "always"]**

semi, quotes 또한 rules page 에서 기능을 확인할 수 있으며, 배열 값 조정을 통해 에러 정도를 설정할 수 있다..

- "off" or 0 : 검사하지 않음
- "warn" or 1 : 노란줄로 경고 표시
- "error" or 2 : 붉은줄로 에러 표시<br>

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcF7Uey%2FbtqGX6dY2sC%2FcKtcjZWL9dokimZKFug8S1%2Fimg.png">
<br>

**우리는 "error"로 해주었기 때문에 빨간색 줄이 잘 그이는 걸 볼 수 있다.**
<br>
<br>

# 1-3 ESLint 설정
<br>

## 위 설정 외에도 여러가지 설정들이 있다.

### 1. 파서 옵션 (parserOptions)
### 2. 파서 (parser)
### 3. 프로세서 (processor)
### 4. 환경(env)
### 5. 플러그인 (plugin)
### 6. 확장 (extends)
<br> 

#### 등 이 있고 이 설정들은 필요할 때 찾아서 써보는걸로!!


