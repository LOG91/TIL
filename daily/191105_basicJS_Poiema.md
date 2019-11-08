## 191105TIL (JS의 역사)

### JS의 발전과 SPA

자바스크립트이 범용적인 언어로 발전하게 되었고 웹 애플리케이션도 데스크톱 애플리케이션과

비교해도 손색없는 사용자 경험을 제공하는 것이 필수가 되었다

더불어 개발 규모와 복잡도도 상승했다 따라서 이전의 개발 방식으로는 복잡해진 개발 과정을

수행하기가 어려웠고 이런 필요에 따라 많은 패턴과 라이브러리가 출현했다

그렇게 SPA(Single Page Application)이 대중화되게 되었고 Angular, React, Vue의 시대가

오게 된 것이다!

### JS는 인터프리터 언어다

자바스크립트는 개발자가 별도의 컴파일과정을 거치지 않는 인터프리터 언어다



### Node.js 와 브라우저 JS

둘 다 ECMAScript표준을 따르고 있고 JS엔진을 내장하고 있기 때문에 자바스크립트로 둘 다

동작이 가능하다 하지만 둘의 목적 자체가 다르다

브라우저 사이드는 HTML과 CSS를 이용하여 렌더링을 하는 목적이지만 Node.js는 다르다

공통적인 ECMAScript외에 제공되는 것 또한 다르다 예를 들면브라우저쪽에는 DOM API가 있지만

Node쪽에는 File 시스템이 있다

이처럼 브라우저는 ECMAScript와 DOM, BOM, Canvas, XMLHttpRequest, Fetch,

requestAnimationFrame, SVG, Web Storage, Web Component, Web worker와 같은

클라이언트 사이드 Web API를 지원한다. Node.js는 클라이언트 사이드 Web API는 지원하지 않고

ECMAScript와 Node.js 고유의 API를 지원한다.



### script 태그의 위치가 중요한 이유

HTML파서는 script태그를 만나게 되면 DOM생성 프로세스를 블로킹 하고 자바스크립트 엔진에

제어권한을 넘긴다 그리고 엔진은 script 태그 내의 자바스크립트 코드를 다 실ㄹ행하고 나서

HTML파서로 다시 제어권을 넘긴다

그래서 body요소의 가장 아래에 script를 많이 위치시킨다

- 중간에 블로킹되어 랜더링에 지장을 받지 않도록
- DOM이 완성되지 않은 상태에서 JS가 DOM을 조작하면 에러가 발생하기 때문에



