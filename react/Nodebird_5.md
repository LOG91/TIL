# Nodebird Clone Coding - 5
### ORM
Object Relational Mapping

원래 SQL문을 알아야 DB를 다룰 수 있지만 자바스크립트 코드만으로

SQL문을 다룰 수 있게, 연결해주는 것을 말한다

본 프로젝트에서는 시퀄라이즈를 사용했다

### Front와 Back의 통신
우리가 접속하는 웹사이트에서 수없이 일어나는 일은 서버와의 통신이다

페이지를 불러오고 싶다면 페이지를 서버에 요청하고 서버에서는 응답하여 그 페이지를 보내준다

로그인을 한다면 로그인 정보가 유효한지를 서버에 물어보고 서버에서 유효한지를 알려준다

게시글 등록, 트윗, 로그인 정보 등록 다 마찬가지다

http통신을 이용하여 프론트와 백이 소통하는 것이다

거기에는 약속이 필요하다

지금은 REST API와 graphQL이 대표적이다

### 웹사이트 접속은 GET 요청이다
페이지에 접속해서 페이지를 불러오는 것은 GET요청을 이용한다

따라서 새로고침은 GET을 하는 것이다

### mysql - knex - sequelize/typeorm
mysql모듈을 이용해서 코드를 짜려면 문자열로 코딩을 해야 한다 쌩쿼리를 짜는 것이다

당연히 버그 잡기도 어렵고 오타가 날 확률도 올라간다

그렇기 때문에 적어도 knex를 이용하는 것을 추천하고 sequelize를 이용해서 짜는 것 또한 좋다

### API란?
api는 정의하기가 항상 애매했었는데 ZeroCho님은 이렇게 정리하셨다
`다른 서비스가 내 서비스의 기능을 실행할 수 있게 열어준 창구`

### MiddleWare
backend의 코드에서 `app.use(~~~)` 와 같은 코드를 많이 보았다

이 코드는 미들웨어를 등록시키는 코드다

요청과 응답 사이에 존재해서 요청과 응답을 살짝 변화시켜주는 역할을 한다

### cookie & session
사용자 정보는 서버의 세션에, 프론트에는 세션을 조회할 수 있는 쿠키를 저장한다!

### 모듈은 캐싱이 된다
sagas/user.js 파일에 아래와 같이 선언이 되어 있다
```js
axios.defaults.baseURL = 'http://localhost:3065/api';
```

하지만 이것은 다른 파일에서도 동일하게 적용된다

파일구조상으로 볼 때도 어색해보이지만 모듈로 불러온 파일은 캐싱을 하게 되어서

모든 파일에 적용이 된다고 한다

그렇기 때문에 루트가 되는 파일에 명시해주는 것이 가장 보기에도, 이해하기에도 좋다

### db조회 시에는 에러처리를 해주는 것이 좋다
try catch 문을 사용하여 처리하도록 한다