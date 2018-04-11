## for ... of
for...of문은 반복가능한 객체 (Array, Map, Set, String, TypedArray, arguments 객체 등을 포함)에 대해서 반복하고 각 개별 속성값에 대해 실행되는 문이 있는 사용자 정의 반복 후크를 호출하는 루프를 생성합니다.

> for...of 구문은 컬렉션 전용입니다, 모든 객체보다는. [Symbol.iterator] 속성이 있는 모든 컬렉션 요소에 대해 이 방식으로 반복합니다. __from MDN__
### for, forEach, for...in
위의 여러 반복문과 같은 기능을 한다
```js
let arr = ['log91', 'whale', 'killerWhale'];
for(let i of arr){
  console.log(i);
}
// log91
// whale
// killerWhale 출력
```
__String에도 적용할 수 있다!__
```js
let str = 'whale';
for(let i of str){
  console.log(i); // w, h, a, l, e 출력
}
```
이 외에 Map, Set, TypedArray, arguments에도 적용 가능하다  

### for...of VS for...in
비슷한 동작을 하지만 for in은 객체에서 많이 사용한다  
물론 배열도 객체이기에 사용가능하지만 사용할 때 문제점이 발생한다
```js
Object.prototype.objCustom = function () {};
Array.prototype.arrCustom = function () {};

let iterable = [3, 5, 7];
iterable.foo = "hello";

for (let i in iterable) {
  console.log(i); // logs 0, 1, 2, "foo", "arrCustom", "objCustom"
}

for (let i of iterable) {
  console.log(i); // logs 3, 5, 7
}
```
### Comment
일단은 객체라면 for in을 사용하지만 배열이라면 for of 사용을...