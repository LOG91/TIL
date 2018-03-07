## Array.indexOf()
indexOf() 함수는 아래와 같이 두 가지 파라미터를 받을 수 있다  
```js
arr.indexOf(searchElement)  
arr.indexOf(searchElement, fromIndex)  
```

serachElement는 배열에서 찾을 요소다  
fromIndex는 배열을 찾기 시작할 인덱스다
```js
var arr = [1,3,5,7,9,1];
arr.indexOf(1) -> 0 // 1의 인덱스인 0을 반환한다
arr.indexOf(5) -> 2 // 5의 인덱스인 2를 반환한다
arr.indexOf(120) -> -1 // 배열에 없는 값을 입력하면 -1을 반환한다

//fromIndex는 검색을 시작할 색인을 입력하는 곳이다  
arr.indexOf(1, 3) -> 5 // 1을 3부터 찾기 시작하기 때문에 뒤의 1의 인덱스인 5가 반환된다
arr.indexOf(1,7) -> -1 // 인덱스가 배열의 길이보다 크거나 같은 경우에는 -1을 반환한다
arr.indexOf(1, -3) -> 5 // 음수 값을 넣는다면 뒤에서부터 검색하여 5가 반환된다
arr.indexOf(1, -1) -> -1 // -1을 넣는다면 -1만 반환한다...

var arr2 = [2, 3, 10, 11];

for(var i = 0; i < arr.length; i++) {
    if(arr2.indexOf(arr[i]) > -1) console.log(arr[i] + '값 중복됨!');
} -> '3 중복됨!'
// 이런 식으로 arr과 arr2의 배열의 중복 검사에 사용할 수 있다!!
```

## Comment
indexOf 비교적 쉬운 함수지만 쓸모가 많은 것 같다