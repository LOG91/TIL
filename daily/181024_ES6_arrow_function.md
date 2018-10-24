# 181024 TIL (ES6 Arrow Function)

화살표 함수(Arrow Function)은 function 키워드 대신에 화살표 (=>) 를 사용하여 보다

간결하게 함수를 선언할 수 있는 ES6에 추가된 문법이다

### 1. 선언

아래에서 여러가지 사용 방법을 살펴보자

```js
const whale = () => {...} // 매개변수가 없을 경우, 소괄호 생략 불가
const whale = x => {...} // 매개변수가 한 개인 경우 소괄호 생략 가능
const whale = (x, y) => {...} //매개변수 여러 개, 소괄호 생략 불가

const whale = x => {return x*x}
const whale = x => x*x //함수 몸체가 한 줄의 구문이라면 중괄호 생략 가능

const whale = () => {a:1} // undefined 반
const whale = () => ({a:1}) // 객체 반환 시에는 소괄호 사용해야 한다
```



### 2. 호출

화살표 함수는 익명 함수로만 사용할 수 있다 따라서 위에 선언처럼 함수 표현식만 가능하다

콜백함수를 쓸 때 간결하기에 많이 사용한다 (물론 상황에 따라서다 this바인딩 때문에..)



### 3. this

Core Part다!

function 키워드로 선언한 함수와 arrow function의 가장 큰 차이는 **this바인딩**이다!

JS에서는 함수 호출 방식에 의해 this가 결정된다 선언될 때 정적으로 결정되는 것이 아니라는

것이다 lexical scope와는 조금은 상반된 개념이다

일반 함수에서는 this는 늘 전역을 가리킨다

그런 점 때문에 콜백함수에서 예상과 다른 this바인딩으로 문제가 발생한다

그래서 그런 문제를 해결하기 위해 여러 가지 방법을 사용해왔다

that에 저장한 후 그것을 콜백에 넣어주거나, bind를 사용하기도 했다



#### 3.1 Lexical this

이 때 화살표 함수를 사용하면 쉽게 해결이 가능한 경우가 많다

화살표함수는 선언될 때에 this에 바인딩할 객체가 정적으로 결정되기 때문이다

동적으로 결정되는 일반 함수와 다르게 언제나 상위 스코프의 this를 가리킨다

> 화살표 함수의 this바인딩의 결정 방식은 함수의 상위 스코를 결정하는 Lexical Scope와 유사하다

또 화살표함수는 call, apply, bind메소드를 사용하여 this변경이 불가능한 특징이 있다



### 4. 화살표 함수를 사용하면 안되는 경우

화살표 함수는 Lexical this를 지원하므로 콜백 함수로 사용하기 편리하다. 하지만 화살표 함수를 사용하는 것이 오히려 혼란을 불러오는 경우도 있으므로 주의하여야 한다.

#### 4.1 메소드

```js
const person = {
    name: 'Whale',
    sayHI: () => console.log(`Hi ${this.name}`)
};
person.sayHI(); // Hi undefined
```

상위 객체인 window를 가리키므로 오류 발생

#### 4.2 prototype

#### 4.3 생성자 함수

화살표 함수는 prototype 프로퍼티를 가지지 않는다

#### 4.4 addEventListener

```js
var button = document.getElementById('myButton');

button.addEventListener('click', () => {
  console.log(this === window); // => true
  this.innerHTML = 'Clicked button';
});
```

위와 같은 문제가 발생한다

하지만 나는 지금껏 여기에 화살표함수를 넣어서 클래스 내부의 함수를 잘 썼는데

클래스 안에서 사용할 경우에 클래스 자신을 가리켜서 괜찮지 않나 싶다



### Comment

아직 this문제로 난항을 겪어본 적이 적어서 공감이 덜된다..

하지만 무슨 말 하는지는 알 수 있는 Arrow Function 공부였다



### Reference

- Poiema Web