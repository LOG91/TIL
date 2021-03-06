# 180727 TIL (Cookie & Cache)

쿠키와 캐시를 사용하는 이유는 서버가 사용자에게 빠른 검색 결과를 제공하기 위함이다

HTTP 통신의 원칙은 Stateless다

클라이언트의 정보를 가지지 않는 서버의 처리 방식을 말한다

하지만 실제 서비스에서는 Stateful한 방식이 필요한 경우가 많다

Stateful을 가능하게 만드는 방법으로 **쿠키와 세션**이 있다

두 개의 차이는 정보를 어디에 저장하는 지다

쿠키는 클라이언트 측, 세션은 서버 측이다

### 쿠키 (Cookie)

쿠키는 클라이언트 로컬에 저장되는 키와 값이 들어 있는 작은 데이터다

쿠키에는 이름, 값, 만료날짜(쿠키 저장기간), 경로 정보가 들어있다

쿠키는 일정시간동안 데이터를 저장할 수 있다

주로 저장되는 정보로는 특정 웹사이트나 웹페이지에 얼마나 자주 또는 몇 번 방문했는지

그리고 특정 배너를 클릭을 했는지 했으면 얼마나 자주 했는지 검색 시 어떤 키워드를

사용했는지 등의 정보들이다

##### SessionCookie

만료 시간을 설정하고 메모리에만 저장되며 브라우저 종료시 쿠키를 삭제한다

#### 사용 사례

- 팝업창 "오늘 더 이상 이 창을 보지 않음" 체크
- 쇼핑몰의 장바구니

#### 쿠키를 이용한 통신 과정

1. 최초 통신에서는 클라이언트가 서버의 쿠기를 가지고 있지 않은 상태에서 request
2. 서버는 request의 헤더에 쿠키가 포함되어 있지 않은 것을 판단하고, 통신의 상태(유저ID, 패스워드, 조작상태, 방문횟수 등)를 저장한 쿠키를 response한다
3. 클라이언트의 브라우저가 받은 쿠키를 보존한다
4. 두 번째 연결에서 HTTP헤더에 쿠키를 실어서 서버에 request한다
5. 서버는 받은 쿠키로부터 클라이언트를 판별한다

#### 쿠키의 제약 조건

- 클라이언트는 총 300개의 쿠키를 저장할 수 있음
- 하나의 도메인 당 20개의 쿠키를 가질 수 있음
- 하나의 쿠기는 4096byte까지 저장 가능

쿠키는 텍스트 형식으로 저장되며 쿠키가 사라지는 시점은 쿠키를 저장할 때 설정할 수 있고

만약 설정하지 않으면 해당 브라우저 종료시 삭제된다

#### 쿠키의 문제점

쿠키는 사용자의 로컬에 저장되고 자유롭게 열람이 가능하다

이같은 특성 때문에 보안에 문제를 겪는데 그래서 중요한 정보는 쿠키로 처리를 하면 안된다





### 캐시 (Cache)

캐시는 이미지나 css, js파일 등이 사용자의 브라우저에 저장되는 것이다

이를 이용해 자원이 아껴지는 것이다 통신량이 줄어들어 속도가 빨리지는 것

쿠키와의 다른 점은 캐시는 이미지와 같은 큰 파일을 저장해두어서 매번 데이터를 과하게 통신하지 않는, 즉 페이지 로딩 속도만을 위함이다

#### 문제점

한 번 캐시에 저장되면 브라우저를 참고하기 때문에 서버에서 변경이 되어도 사용자는 변경이 되지 않게 보일 수 있는데 이런 부분을 캐시를 지워주거나 서버에서 클라이언트로 응답을 보낼 때 header에 캐시 만료 시간을 명시하는 방법을 이용할 수 있다



### 쿠키와 캐시의 차이점

캐시는 오로지 페이지 로딩 속도를 위하여 로컬을 임시저장소처럼 이용하는 것이다

쿠키는 User preference (유저가 웹사이트 접속 시 하는 행동 패턴 또는 관련 정보) 위주의

정보를 저장한다