# Object.assign()
객체를 복사해서 immutable객체를 반환한다  
단순히 복사하는 것이 아니라 여러 객체를 병합할 수도 있다

## 문법
Object.assign(target, ...sourcesObject)  

## 사용
### 복사
```js
const obj = {
    name : 'whale',
    age : 28
};
const obj2 = {
  name : 'log91'
}
const copy = Object.assign(obj,obj2);
// copy -> {name : 'log91', age : 28};

const copy2 = Object.assgin({},obj);
// 빈 객체를 넣어줘서 복사된 객체를 반환할 수 있다
copy === copy2 // false
// immutable이기 때문에 false를 반환한다
```
### 병합
```js
var o1 = { a: 1 };
var o2 = { b: 2 };
var o3 = { c: 3 };

var obj = Object.assign(o1, o2, o3);
console.log(obj); // { a: 1, b: 2, c: 3 }
console.log(o1);  // { a: 1, b: 2, c: 3 } o1은 타겟이기에 값이 변경된다
// 그리고 o1 === obj는 false이다!

// 위처럼 타겟이 변하는 것은 문제가 될 수 있다
// 그 때에는 아래와 같은 방법을 사용할 수 있다
// 그 때에 o1의 변경을 막을 수 있다!
var o1Target = JSON.parse(JSON.stringify(o1));

```
```js
var o1 = { a: 1, b: 1, c: 1 };
var o2 = { b: 2, c: 2 };
var o3 = { c: 3 };

var obj = Object.assign({}, o1, o2, o3);
console.log(obj); // { a: 1, b: 2, c: 3 }
```
같은 프로퍼티를 가지고 있다면 인수의 순서에 따라 덮어쓴다

## Comment
- Object를 사용하게 될 일이 많을 것 같은데 아주 유용한 함수 같다  
- 클래스의 상속같은 개념이 아닐까 생각이 든다