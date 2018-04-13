# Set
```js
new Set();
```
new Set()으로 생성하고 () 안에 넣은 값들로 초기화 시켜준다. 매개변수가 없다면 빈 상태로 만들어진다  

> Set 객체는 값 컬렉션으로, 삽입 순으로 그 요소를 반복(iterate)할 수 있습니다. Set 내 값은 한 번만 발생할 수 있습니다. 즉, 그 값은 Set 컬렉션 내에서 유일합니다.  
from MDN  

set의 가장 큰 특성은 중복된 값이 들어가지 않는 다는 것이다  
그리고 기존 array의 메소드를 사용할 수 없다  
추가로 undefined와 null도 저장이 가능하고 NaN도 가능하다  
원래 자바스크립트에서 NaN === NaN은 false지만 Set에서는 __같은 값__ 으로 간주한다

### Method
- add(value) : 새로운 요소 value를 추가하고 set객체를 반환한다  
- size() : set의 길이를 반환한다 
- clear() : 모든 요소를 삭제한다
- delete(value) : value 요소를 삭제한다 has(value)가 이전에 반환했던 값을 반환하고  
이후로는 false를 반환한다  
- has(value) : value값이 있는 지에 따라 boolean 값을 반환한다  
- forEach : 사용가능하다!!

### Example
```js
var mySet = new Set();
mySet // Set(0) {}
mySet.add(2); // Set(1) {2}
mySet.add(5); // Set(2) {2, 5}
mySet.add(5); // Set(2) {2, 5} 중복을 허용하지 않기 때문에 같다

mySet.add('whale'); // Set(3) {2, 5, 'whale'}
mySet.add({a:1,b:2}); // Set(4) {2, 5, 'whale', {a:1,b:2}}

mySet.has(2); // true
mySet.has(3); // false 객체 안에 3은 없다

```

### Array와 Set
```js
var arr = ['whale', 'log91', 'killerWhale'];
// 아래와 같이 사용하면 array를 set으로 변환한다
var set = new Set(arr);

// spread operator를 사용하면 배열로 변환이 가능하다
console.log([...set]); // arr과 같은 배열이다
set.push(1); // ['whale', 'log91', 'killerWhale', 1];
```
### Comment
알고리즘을 풀 때 많이 사용되는 것 같다