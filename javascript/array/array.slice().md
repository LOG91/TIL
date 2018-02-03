## Array.splice()
**1. Use**
```
I have an array, I would like to add items or other arrays
I need to add element/s to an array

or

I have an array, I would like to remove items
I need to remove element/s from an array
```

**2. Splice**

splice 메서드는 원하는 위치에 요소를 추가하거나 요소를 삭제할 수 있는 두 가지를 구현할 수 있다

**3. Code**
```js
var arr = ['apple', 'banana', 'ccc'];
// 배열 추가
arr.splice(2, 0, 'delta'); // 'delta'를 두번째 인덱스에 삽입 

// 배열 삭제
arr.splice(2,1); // 두번째 인덱스에서 하나의 항목 'ccc'를 삭제
```

**4. Output**
```js
// 배열 추가
arr = ['apple', 'banana', 'delta', 'ccc']; 

// 배열 삭제
arr = ['apple','banana']; 

```