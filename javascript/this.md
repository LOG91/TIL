# JS의 this
프로그래밍 언어에는 this가 들어가 있다

그리고 일반적으로 this는 객체 자신을 가리킬 때 사용한다

그래서 다른 객체의 값들과 비교되는 나를 가리키게 할 수 있어 여러모로 유용하게 사용된다

하지만 JS의 this는 좀 다르다 다른 언어의 개발자들이 js개발에 많이 혼란을 겪는 파트 중의 하나다

### 함수 호출 방식에 따라 다르게 binding되는 this
자바스크립트의 경우 함수 호출 방식에 의해 this에 바인딩할 어떤 객체가 동적으로 결정된다.

다시 말해, 함수를 선언할 때 this에 바인딩할 객체가 정적으로 결정되는 것이 아니고,

함수를 호출할 때 함수가 어떻게 호출되었는지에 따라 this에 바인딩할 객체가 동적으로 결정된다.

함수의 상위 스코프를 결정하는 방식인 렉시컬 스코프(Lexical scope)는 함수를 선언할 때 결정된다.

this 바인딩과 혼동하지 않도록 주의하기 바란다.

#### 함수 호출 방식 네 가지
- 함수 호출
- 메소드 호출
- 생성자 함수 호출
- apply/call/bind 호출

#### 1. 함수 호출
전역객체는 전역 스코프(Global Scope)를 갖는 전역변수(Global variable)를 프로퍼티로 소유한다.

글로벌 영역에 선언한 함수는 전역객체의 프로퍼티로 접근할 수 있는 전역 변수의 메소드이다.

기본적으로 this는 전역객체(Global object)에 바인딩된다.

전역함수는 물론이고 심지어 내부함수의 경우도 this는 외부함수가 아닌 전역객체에 바인딩된다.

또한 메소드의 내부함수일 경우에도 this는 전역객체에 바인딩된다.

```js
function foo() {
  console.log("foo's this: ",  this);  // window
  function bar() {
    console.log("bar's this: ", this); // window
  }
  bar();
}
foo();

var value = 1;

var obj = {
  value: 100,
  foo: function() {
    console.log("foo's this: ",  this);  // obj
    console.log("foo's this.value: ",  this.value); // 100
    function bar() {
      console.log("bar's this: ",  this); // window
      console.log("bar's this.value: ", this.value); // 1
    }
    bar();
  }
};

obj.foo();
```
콜백함수의 경우에도 this는 전역객체에 바인딩된다.
```js
var value = 1;

var obj = {
  value: 100,
  foo: function() {
    setTimeout(function() {
      console.log("callback's this: ",  this);  // window
      console.log("callback's this.value: ",  this.value); // 1
    }, 100);
  }
};

obj.foo();

```
내부함수는 일반 함수, 메소드, 콜백함수 어디에서 선언되었든 관게없이 this는 전역객체를 바인딩한다.

더글라스 크락포드는 “이것은 설계 단계의 결함으로 메소드가 내부함수를 사용하여 자신의 작업을 돕게 할 수 없다는 것을 의미한다” 라고 말한다.

해결할 수 있는 방법은 있다

1.
```js
const nickname = 'log91';
const obj = {
  nickname: 'whale',
  fn1: function() {
    var that = this;
    function fn2() {
      console.log(this.nickname); // 'log91'
      console.log(that.nickname); // 'whale'
    }
  }
}
```
2. call, apply, bind 함수를 이용해서 명시적으로 객체를 정해주는 방법

#### 3. 생성자 함수 호출
생성자는 말그대로 객체를 생성하는 역할을 한다

방법은 함수 앞에 new키워드를 붙여주는 것이다 이 말은 일반함수 앞에도 new를 붙이면 가능하다는 것이다

그래서 구별해주기 위하여서 생성자함수는 맨 앞 문자를 대문자로 표기한다 `new Person()`

new 연산자와 함께 생성자 함수를 호출하면 this 바인딩이 메소드나 함수 호출 때와는 다르게 동작한다.

##### 3.1 생성자 함수 동작 방식
###### 1. 빈 객체 생성 및 this 바인딩
생성자 함수의 코드가 실행되기 전 빈 객체가 생성된다

이 빈 객체가 생성자 함수가 새로 생성하는 객체이다. 이후 생성자 함수 내에서 사용되는 this는 이 빈 객체를 가리킨다

그리고 생성된 빈 객체는 생성자 함수의 prototype 프로퍼티가 가리키는 객체를 자신의 프로토타입 객체로 설정한다.


## Reference
- Poiema Web (https://poiemaweb.com/)

