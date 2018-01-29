# 팩토리얼 (Factorial)

## 문제
```
In mathematics, the factorial of a non-negative integer n, denoted by n!,
 is the product of all positive integers less than or equal to n. 
 For example: 5! = 5 * 4 * 3 * 2 * 1 = 120. By convention the value of 0! is 1.

Write a function to calculate factorial for a given input. 
If input is below 0 or above 12 throw an exception of type ArgumentOutOfRangeException (C#) 
or IllegalArgumentException (Java) or RangeException (PHP) or throw a RangeError (JavaScript).
```

### 나의 풀이
```js
function factorial(n)
{
  // Calculate the factorial here
  if(n<0 || n>=12) throw RangeError;
  let sum = 1;
  for(let i = 1; i <= n; i++){
    sum *= i;
  }
  return sum;
}
```

### Best Practices
```js
function factorial(n) {
  if (n < 0 || n > 12)
    throw new RangeError();
  return n <= 1 ? 1 : n * factorial(n - 1);
}
```

### Comment
factorial이라는 함수가 있다는 사실을 알았다.  
몇 문제 안 풀었지만 등급이 7kyu로 랭크업되었다.. 
