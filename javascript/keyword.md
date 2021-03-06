# 학습키워드 정리

## 1. 비트연산자 보수
비트 연산자는 피연산자를 10진수, 16진수, 8진수처럼 취급하지 않고  
32비트의 집합으로 취급한다  
1 & 2 와 10 | 14 이런식으로 두 인자로 연산한다  
#### 주요 비트연산자를 요약한 표  

| 연산자 | 사용법 | 설명 |
|--------|:--------:|------|
|비트 AND| a&b  | 두 피연산자의 대응되는 비트가 모두 1이면 1 반환 |
|비트 OR| a \| b  | 두 피연산자의 대응되는 비트가 둘 중 하나가 1이거나 모두 1인 경우 1 반환 |
|비트 XOR| a ^ b  | 두 연산자의 대응되는 비트에서 둘 중 하나가 1이고, 둘 다 1이 아닐 경우 1 반환 |
|비트 NOT| ~a  | 피연산자의 비트를 뒤집음|

#### 보수  
예를 들어 26을 2진수로 표현하면 11010인데 이것을 비트연산자 32비트의 집합으로 표현하면  
0000 0000 0000 0000 0000 0000 0001 1010 이 된다  
여기서 비트를 반전시키면  
1111 1111 1111 1111 1111 1111 1110 0101 이 된다  
이것을 1의 보수방법이라고 하고 2의 보수방법은 1의 보수에 1을 더하기만 하면 된다  
26의 2진수 값과 26의 2의 보수를 더하면 0이 나온다

## 2. Hoisting
>Hoist : 끌어 올리다

호이스팅(Hoisting)은 코드 아래에서 변수가 선언되었지만 마치 위에서 선언된 것처럼  
코드 아래의 변수의 선언만 끌어올려서 사용하는 효과를 말한다  
예를 들어 보겠다
```js
console.log(str); // 에러가 나지 않고 undefined가 뜬다 아래의 var str;만 호이스팅된 것이다
var str = 'whale';
```
함수도 변수이기에 호이스팅된다  
아래와 같이 함수 선언식으로 선언한다면 통째로 위로 호이스팅되고  
표현식으로 한다면 호이스팅되지 않기에 에러가 난다
```js
showName('log91'); // log91
showName2('whale'); // showName2 is not a function
function showName(name) {
  console.log(name);
};
var showName2 = function(name) {
  console.log(name);
};
```

## 3. !!
!는 부정을 의미한다  
예를 들어 !true는 false !false는 true이고  
0은 false값이기에 !0은 true를 나타낸다  
!!는 결국 이중부정을 의미하는데 무슨 의미가 있을까 싶지만  
어느샌가 논리타입 boolean으로 바뀐 것을 발견할 수 있을 것이다

## 4. 3개 이상의 switch문을 어떻게 3항연산자로 대체할까? (코드예시)
```js
switch(name) {
  case whale : 
      console.log('whale은 고래~');
      break;
  case dolphin :
      console.log('dolphin은 돌고래~');
      break;
  case killerWhale :
      console.log('killerWhale은 범고래~');
      break;
}
// 아래는 3항 연산자로 대체한 식
(name === 'whale') ? console.log('whale은 고래~') : (name === 'dolphin') ? console.log('dolphin은 돌고래~') : console.log('killerWhale은 범고래~');
// 이런 식으로 n개까지 가능할 것으로 예상된다
```

## 5. ==와 ===의 차이는 정확히 무엇인가?
==는 자바스크립트 내부의 규정(?)을 따라 타입별로 알아서 형변환 후 비교한다  
느슨한 같음(loose equality)라고도 한다  
> 1 == '1'이 true를 반환한다

이와 다르게 ===는 ==보다 엄격하게 타입까지 비교한다  
엄격한 같음(strict equality)라고도 한다  
> 1 === '1'이 false를 반환한다

## 6. const value = a || b; 코드의 의미는 무엇인가?
||는 논리 연산자다  
결과적으로 a || b 가 있을 때 a가 true면 a를 리턴하고 false값이라면 b를 리턴한다    
그동안 if(a === 1 || b === 1){} 이런식으로 조건식에 많이 사용했었는데  
이렇게도 사용할 수 있는 이유는 조건식이 성사될 때 리턴하는 값이 true or false가 아니라  
__실제 자신의 값을 리턴__ 하기 때문이다  
아래 예와 같이 크로스 브라우징 할 때에 많이 사용된다고 한다  
```js
function test(e) {
        e = e || window.event; // e 가 존재할 경우, e로 설정하고 없을 경우 window 속성의 event 로 설정한다
        ...(중략)
    }
```

## 7. eval은 무엇인가?
문자로 표현된 javascript코드를 실행하는 함수다  
```
eval('1 + 2') // 3을 반환한다.
eval('if(true)console.log("Happy coding")'); // Happy Coding을 반환한다.

// 아래와 같이string이 아닌 객체값으로 받아주면 그대로를 반환한다
eval(new String("2 + 2")); // "2 + 2" 반환
```
마지막 표현식이 반환된다
```
eval('x = 123'); // 123를 반환
eval('x = 123, y =242'); // 242를 반환
eval('x = 123, y =242, z = 124'); // 124를 반환

// 조건식을 사용할 때
var str = "if ( a ) { 1+1; } else { 1+2; }";
var a = true;
var b = eval(str);  // 2를 반환

console.log("b is : " + b);

a = false;
b = eval(str);  // 3을 반환

console.log("b is : " + b);

// 아래와 같이 사용할 수도 있다
var dateFn = "Date(1991,8,13)";
var myBirth;
eval("myBirth = new " + dateFn + ";");

document.write(myBirth);
```
자바스크립트 코드 최적화의 측면에서 eval()함수는 자제수준이라고 한다 바로 실행시키는 것이 보안상 위험하다고 한다!

## 8. 변수값을 출력할때 null, undefined, is not defined으로 출력되는 차이점은 무엇인가?
1. __null__  
null은 내가 임의로 var a = null 이런식으로 지정해줘야 나오는 값  
2. __undefined__  
변수는 선언되었는데 아무 값도 초기화되어있지 않을 때 나오는 값  
3. __is not defined__  
해당 변수가 아예 선언되지 않았을 때 나오는 값  

## 9. Function.prototype.bind 에 대해서 설명하기
bind는 쉽게 말하면 함수와 객체를 묶어주는 역할을 한다고 볼 수 있다  
```js
function hi() {
    return 'Hi, ' + this.name;
}
const obj = {name : 'ES6'};
hi(); // 이렇게 하면 name값이 없는 hi함수는 Hi, 까지만 출력한다

hi.bind(obj); // bind를 이용한다면 Hello ES6를 출력한다

// 아래는 mdn에 나와있는 예제다
this.x = 9;
var module = {
  x: 81,
  getX: function() { return this.x; }
};

module.getX(); // 81

var retrieveX = module.getX;
retrieveX();

var boundGetX = retrieveX.bind(module);
boundGetX(); // 81
```

## 10. this가 가리키는 것은 언제 결정되는가
일반적으로 this는 객체의 프로퍼티인 함수에서 의미가 있다.  
메서드를 호출하면 this는 호출한 메서드를 소유하는 객체가 된다.  
this는 함수를 어떻게 선언했느냐가 아니라 어떻게 호출했느냐에 따라  
달라진 다는 것을 이해해야 한다.  
```js
const o = {
    name : 'Wallace',
    speak() {return `My name is `+ this.name}
}

o.speak(); // Wallace를 호출

const speak = o.speak;
speak === o.speak; // true 같은 함수를 가리킨다
speak() //My name is undefined 호출
```
위 식에서 speak가 호출될 때 어디에서 호출됐느냐가 this가 무엇을 가리키는지가 결정되는 것이다  
  결론적으로 this는 함수가 호출되는 지점의 객체를 참조하다고 볼 수 있다  
  
## 11. call과 apply의 차이점은?
원래 함수는 선언한 후에 호출해야 하고 함수 뒤에 ()를 붙여서 호출하지만  
다른 두 가지 방법, 여기에 call 과 apply써서 호출할 수 있는 방법도 있다  
역시 이름만 다른 것이 아니고 그냥 ()와는 다른 기능이 있다 아래 예를 들겠다  
```js
var obj = {
  name: 'whale',
  callName: function() {
    console.log(this.name);
  }
};
var obj2 = {
  name: 'log91'
};
obj.callName(); // whale 호출
obj.callName.call(obj2); // log91호출
```
위의 예처럼 call을 써서 인자에 객체를 넣어줄 때에  
그 객체의 프로퍼티를 참조해서 사용한다  
call 과 apply의 차이는 call은 매개변수를 그대로 나열하지만  
apply는 배열로 만들어서 넣어줘야 한다

## 12. add(10)(2) //12 가 되도록 구현해보기
```js
function add(v1) {
  function add2(v2) {
    return v1 + v2
  }
  return add2
}
console.log(add(10)(2)); // 12
```

## 13. 함수의 인자갯수와 파라미터가 일치하지 않으면 어떤일이 생기는가 설명하기
```js
function fn(a, b, c) {
    console.log(a, b, c); 
}

fn(1); // 1 undefined undefined
fn(1, 2) // 1 2 undefined
fn(1, 2, 3) // 1 2 3

fn(1, 2, 3, 4, 5, 6) // 1 2 3
```
위의 예처럼 자바스크립트는 파라미터의 개수가 적거나 넘어도 오류가 나지 않고  
없는 값에 대해서는 undefined를 호출해주고 인자 개수가 넘어가면 자연스럽게 없는 것처럼..? 넘어간다

## 14. 함수의 반환값이 없을 때에 어떻게 되는가?  
함수안의 구문은 실행되지만 반환은 undefined로 해준다

## 15. 익명함수는 무엇인가?  
이름이 없는 함수다  
보통 함수는 function abc() {} 의 형태로 만들어서 사용하지만  
다시 사용이 필요없는 함수를 쓸 때 사용한다  
```js
const a = function(){console.log('hello')} // 변수에 넣어줄 때

abc.reduce(function(){}) // 함수의 인자로 들어갈 때

(function(){console.log('hello')})() // 즉시 실행 함수
```