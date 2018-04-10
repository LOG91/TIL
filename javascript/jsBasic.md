## Javascript 기초
자바스크립트 기초 문법
## 1. var, let, const  
var함수는 ES5까지 모든 변수로 사용되어 왔지만 호이스팅의 문제로 개발자들의 원성을 많이 샀었다  
작은 애플리케이션의 경우 전역변수의 선언이 별로 문제가 되지 않고 오히려 편하지만  
애플리케이션이 커질 경우에 심각한 문제가 된다.  

### Scope
대부분의 언어에서 변수는 block-level scope를 갖지만 자바스크립트는 function-level scope를 갖는다  
함수 안에서만 지역 변수로 사용되고 밖에서는 사용할 수 없는 scope인 것이다  
```js
function abc(){
  var a = 'hello';
  for(let i = 0; i < 5; i++) {
    console.log(i);
  }
  console.log(i); // 에러가 뜬다 let으로 선언된 i가 블록스코프이기 때문에 밖에서 참조 X
}
console.log(a); // 에러가 뜬다 변수 a는 function 안에 있기 때문이다
```


### __호이스팅이란?__
JavaScript가 어떤 코드를 실행하기 전에 함수 선언을 메모리에 저장하는 방식이라고 할 수 있다
예를 들어:  
catName("Tigger");  
function catName(name) {
  console.log("My cat's name is " + name);
}


/*
위 코드의 결과는: "My cat's name is Tigger"
*/  
-> 아래의 function을 catName()위로 올려주는 효과라고 볼 수 있다!  

var도 이런 특성으로 아래와 같은 문제들이 발생한다
```js
// 이 경우에도 오류가 나지 않고 출력된다.
for(var j=0; j<10; j++) {
  console.log('j', j)
}
console.log('after loop j is ', j);

// 마찬가지로 오류가 나지 않는다
c = 'test'
var c
```
ES6부터 등장한 let과 const는 var의 문제점을 보완한다
```js
// let
let a = 'test'
let a = 'test2' // Uncaught SyntaxError: Identifier 'a' has already been declared
a = 'test3'     // 가능

// const
const b = 'test'
const b = 'test2' // Uncaught SyntaxError: Identifier 'a' has already been declared
b = 'test3'    // Uncaught TypeError:Assignment to constant variable.
```
let은 재선언은 불가능 해도 재할당은 가능하다  
반면에 const는 재선언, 재할당 모두 에러를 낸다  

### Point
여기서 착각할 수 있는 것은 __let과 const가 호이스팅 되지않는 것처럼__ 느끼는 것이다  
하지만 자바스크립트는 모든 변수를 호이스팅한다  
여기서 알아야할 것이 excution context의 개념인데 아직 공부를 안한 상황...  
그것을 알면 변수가 3단계에 걸쳐서 선언되는 것을 알 수 있다  
1. 선언 단계
2. 초기화 단계
3. 할당 단계
이렇게 3단계로 이루어지는데 
var 키워드로 선언된 변수는 선언 단계와 초기화 단계가 한번에 이루어진다.   
즉, 스코프에 변수가 등록(선언단계)되고 변수는 undefined로 초기화(초기화단계)된다.  
따라서 변수 선언문 이전에 변수에 접근하여도 변수 객체(Variable Object)에 변수가 존재하기 때문에 에러가 발생하지 않는다. 다만 undefined를 반환한다. 이러한 현상을 __변수 호이스팅(Variable Hoisting)__ 이라한다.  
  
  하지만 let 키워드로 선언된 변수는 선언 단계와 초기화 단계가 분리되어 진행된다. 즉, 스코프에 변수가 등록(선언단계)되지만 초기화 단계는 변수 선언문에 도달했을 때 이루어진다. 초기화 이전에 변수에 접근하려고 하면 ReferenceError 에러가 발생한다. 이는 변수가 아직 초기화되지 않았기 때문인데 스코프의 시작 지점부터 초기화 시작 지점까지를 일시적 사각지대(Temporal Dead Zone; TDZ)라고 부른다.
  
## 2. == vs ===  
자바스크립트는 == 비교연산자만 사용할 시에 암묵적으로  
형변환을 해서 0 == '0' -> true 와 같은 결과를 낸다  
=== 를 사용하여 type까지 비교하는 것이 좋다
## 3. 변수 타입 확인
```js
// 이런 식으로 체크한다
var str = 'abc';
typeof str -> string
typeof 123 -> number
typeof true -> boolean
```
typeof null -> object 값이 뜨는데  
toString.call()을 이용하면 더 자세한 정보가 나온다