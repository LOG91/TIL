## Array.map()
### 문법
> arr.map(callback[, thisArg]);
### map이란
map()메소드는 arr의 모든 메소드들을 돌며 callback()을 호출하고  
그 결과를 모아 새로운 배열을 리턴한다.  
callback 함수는 callback(current, index, array)로 구성된다  
- current : 배열의 요소 중 현재 처리되는 요소
- index : 현재 처리되는 요소의 인데스
- array : 본래의 전체 배열  
### map의 특징
- 원래의 배열을 변형하지 않고 새로운 배열을 반환한다
- map이 시작되고 삭제된 요소는 돌지 않는다

### 예시
```js
var numbers = [10, 20, 30];
var dobuleNumbers = numbers.map(function(value){
  return value *2
  });
// numbers = [10, 20, 30];
// doubleNumbers = [20, 40, 60];

var numbers = [14, 29, 30, 150, 23, 44, 12];
number.map(function(v){
  if(v > 30)return v - 30;
return v;
});
// 한 가지 더 예를 들기 위해 괴상한 함수를 만들었는데
// 위처럼 사용한다면 요소가 30보다 큰 값들만 30을 빼서 새로운
// 배열을 만들 수 있다
```
### Comment
문제를 해결하다보면 map함수가 먼저 떠오를 때가 많다  
그만큼 유용하게 쉽게 잘 사용할 수 있다  
더 익숙해지도록 코드를 배워서 응용할 수 있도록 해야겠다