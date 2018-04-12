# Destructuring
배열의 값이나 객체의 속성을 별개의 변수로 추출할 수 있는 ES6 식  
es5로는 긴 구문을 이용해서 추출해야 할 식을 아주 간단하게 만들 수 있다
## Example
### __In Array__
```js
let data = ['whale', 'log91', 'dolphin'];

let gorae = data[0];
let seokki = data[2];
let [gorae,seokki] = data; // gorae = whale, seokki = log91
let [gorae,,seokki] = data; // gorae = whale, seokki = dolphin
// 위와 같이 중간에 공백을 넣으면 해당 엘리먼트는 스킵한다.
```
#### 선언에서 분리할 수도 있다
```js
let a,b;
[a,b] = [1,2]; // a = 1, b = 2
```
#### 기본 값을 지정
```js
let 
let [name= 'whale', age = 28] = ['log91'];
// name = log91, age = 28
```
### __In Object__
객체에서는 조금 다르게(?) 동작한다  
좌측에 선언한 변수명의 값을 객체 내에서 탐색해서 그 값을 반환한다  
물론 찾으며 변수명을 변경하는 것도 가능하다
```js
let obj = {
	name : 'Log91',
	address : 'Korea',
	age : 28
}
// 객체에서 특정 프로퍼티를 추출할 때 아주 유용하다
let {name, age} = obj; // name = 'Log91', age = 28
// 변수 이름을 지정해주는 것도 물론 가능하다
let {name:myName, age:myAge} = obj; // myName : Log91, age = 28
// 변수 이름지정과 초기화도 한꺼번에 가능하다
let {name:myName, age:myAge, job:job='Software engineer'} = obj; // myName : Log91, age = 28, job = Software engineer
```

## Comment
아직 경험해보지 않았지만 json을 다루는데 필수적인 문법이 되지 않을까 생각이 된다  
그리고 ES6가 왜 큰 변화였는지 하나씩 느끼고 있다