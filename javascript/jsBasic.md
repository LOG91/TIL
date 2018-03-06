## Javascript 기초
자바스크립트 기초 문법
## 1. var, let, const  
var함수는 ES5까지 모든 변수로 사용되어 왔지만 호이스팅의 문제로  개발자들의 원성을 많이 샀었다

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