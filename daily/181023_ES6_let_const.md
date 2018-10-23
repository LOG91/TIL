# 181023 TIL (let, const)

한동안 CSS 공부만 계속 해왔는데 환기도 시킬겸 JS공부를 하기 위해 Poiema Web을 뒤져 보다가 (poiema web 개인적으로 사랑) ES6 내용을 다시 훑어 보고 싶어서 하게 되었다

## let과 const

ES6 전에는 변수를 선언하는 유일한 방법은 `var`키워드 였다

하지만 몇 가지 치명적인 문제점들이 있었다 (설계상 오류라고도 한다)

문제점은 아래와 같았다

- 함수 레벨 스코프
- var 키워드의 생략 허용
- 중복 선언 허용
- 변수 호이스팅

### 1. let

#### 1.1 블록 레벨 스코프

함수 레벨 스코프의 문제점은 블록으로는 스코핑이 되지 않기 때문에

for문 안에 쓰인 i마저도 전역변수가 될 수 있다

```js
var foo = 123;
console.log(foo); // 123
{
    var foo = 456;
}
console.log(foo); // 456
```

그리고 위처럼 블록 안에서는 보통 지역변수를 예상하지만 이것이 외부 변수에 영향을

미치게 된다,  중복 선언이 가능하기에 생긴 일이기도 하다

```js
let foo = 123;
{
  let foo = 456;
  let bar = 456;
}
console.log(foo); // 123
console.log(bar); // ReferenceError: bar is not defined
```

let을 사용한다면 블록 레벨 스코프로 위와 같은 결과를 얻는다



#### 1.2 중복 선언 금지

또 var의 문제점 중 하나였던 중복을 허용하지 않는

```js
var whale = 123;
var whale = 456; // 중복 선언 허용

let log91 = 123;
let log91 = 456; // error
```



#### 1.3 호이스팅

호 이 스 팅 이다.. JS를 공부하면 꼭 등장하는 hoisting이다`hoist: 끌어올리다  `

이번에 공부하면서 더 명확하게 이해가 되었다

다들 어느 정도는 알고 있지만 TDZ의 개념이나 변수선언이 3단계에 걸쳐 된다는 개념은

잘 모를 것 같다 (착각일수도)

```js
console.log(foo);
var whale; // undefined

console.log(log91);
let log91; // Errror: Uncaught ReferenceError: log91 is not undefined
```

먼저 변수가 생성되는 3단계의 과정을 살펴 보자

- 선언 단계: 변수를 실행 컨텍스트의 변수 객체(variable object)에 등, 이 변수 객체는 스코프가 참조하는 대상이 된다
- 초기화 단계: 변수 객체에 등록된 변수를 위한 메모리 공간을 확보한다, 이 단계에 변수가 undefined로 초기화된다
- 할당 단계: undefined로 초기화된 변수에 실제 값을 할당

결과적으로 모든 선언(var, let, const, function,class)을 호이스팅한다

변수 var의 경우엔 1,2 단계가 한꺼번에 되면서 밑에서 선언만 된다면 undefined의 값으로 위에서 받아볼 수 있게 된다

하지만 let은 다르다 1단계와 2단계가 분리되어 진행되기 때문에 undefined값이 할당되지 않아 레퍼런스 에러를 내는 것이다!

#### 1.4 전역객체와 let

```js
var whale = 123;
console.log(window.whale); // 123

let killerWhale = 123;
console.log(window.killerWhale) // undefined
```

Poiema에서

let 키워드로 선언된 변수를 전역 변수로 사용하는 경우, let 전역 변수는 전역 객체의 프로퍼티가 아니다. 즉, window.foo와 같이 접근할 수 없다. let 전역 변수는 보이지 않는 개념적인 블록 내에 존재하게 된다

라고 하는데 **보이지 않는 개념적인 블록이 어디인지는 잘 모르겠다..!!!!**

### const

const는 let과 거의 비슷해서 몇 가지 다른 점만 적고 끝내겠다

- let은 재할당이 되는데 const는 재할당이 불가능하다 (객체로 선언시 프로퍼티들은 가능)

- const는 반드시 선언과 동시에 할당이 이루어져야 한다 `const whale; // error`



### Comment

계속 CSS를 공부하다가 오랜만에 JS를 공부하는데 느끼는게 꽤 많았다

개발을 계속 하는 것보다 오히려 틈을 내어 공부를 하는 것이 더 효율적인 것 같다

뇌를 다른 쪽으로도 굴려야 한다고 하는데 그것인가 싶다

그래서 틈틈히 책도 읽고 영어공부도 하려고 한다

그리고 JS를 반복적으로 학습하니 이제 더 머리에 잘 그려진다 (뿌듯!)