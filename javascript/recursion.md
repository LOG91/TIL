## Recursion (재귀)

함수 안에서 함수 자신을 호출하는 프로그래밍 기법  

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

3. 아직 미해결

```js
function findSolution(target) {
  function find(current, history) {
    if (current == target) {
      return history;
    } else if (current > target) {
      return null;
    } else {
      return find(current + 5, `(${history} + 5)`) ||
             find(current * 3, `(${history} * 3)`);
    }
  }
  return find(1, "1");
}

console.log(findSolution(24));
// → (((1 * 3) + 5) * 3)
```

### Use Recursion

- 재귀가 루프보다 3배가량 느리다고 한다 재귀냐 루프냐는 우아함과 효율의 딜레마다, 편하고 코드가 괜찮아 보이기에 사용하지만 성능으로는  더 많은 부담을 주기 때문에 성능이 중요하면 지양하는 것이 좋다

- 재귀를 사용하면 쉽게 풀리는 문제들이 많이 존재한다  
- 성능의 문제가 되기 전까지는 사용해도 무방하다  
- 재귀적 사고를 가질 수 있도록 많이 사용해보는 것이 좋다
  

### Comment

EJS를 통해 재귀를 더 공부하고 있다가 위 3번 예제를 보게 되었는데 지금껏 내가 썼던 재귀는 정말 쉬운, 누구나 생각할 수 있는 재귀였다는 것을 알게됐다

디버깅을 하면서 대략 어떤 방식인지는 알겠는데 저것을 재귀적 생각으로 구현할 생각이 날 것 같지가 않다 재귀적 사고를 많이 연습해야할 것 같다

