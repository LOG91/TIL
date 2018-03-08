## Recursion (재귀)

함수 안에서 자신을 호출하는 프로그래밍 기법  

###  예제
1. countdown
```js
// for문 사용
var count1 = function(n) {
  for(var i = n; i >= 0; i--) {
    console.log(i);
  }
}
// 0,1,2,3,4 ... 출력

// 재귀 사용
var count2 = function(n) {
  console.log(n);
  if(n <= 0) {
    return;
  }
  count2(n-1);
}
```
2. factoiral
```js
// 팩토리얼1 (for문 사용)
function factorial1(num) {
  let result = 1;
  for (let i = num; i >= 1; i--) {
    result *= i;
  }
  return result;
}

// 팩토리얼2 (재귀 사용)
function factorial2(num) {
  let result = 1;
  if (num === 1) return 1;
  return num * factorial2(num - 1);
}
```
- 위처럼 재귀에는 반드시 종료 조건이 필요하다
- 재귀로 구현할 때에 종료 조건을 먼저 정의해놓고 구현하는 것도 팁이다

### 왜 재귀인가
재귀를 사용하면 쉽게 풀리는 문제들이 많이 존재한다  
그리고 많은 곳에 쓰이기 때문에 알아두는 것이 좋다  
재귀적으로 푸는것을 __분할 정복 알고리즘__ 이라고 한다
> 분할 정복 알고리즘 : 어떤 문제를 한 번에 풀기 힘들 떄 작은  
조각으로 쪼개어 푸는 것

재귀를 사용하는 것이 어렵기 때문에 좋아보이지만 성능으로는  
더 많은 부담을 주기 때문에 성능이 중요하면 지양하는 것이 좋다