# Greatest Common Divisor (최대공약수)

최대공약수를 구하는 알고리즘을 구현한다

### 두 수의 최대 공약수를 구하는 함수

```js
function calculateGCD(a, b) {
  let min = Math.min(a, b);
  for (let i = min; i > 0; i--) {
    if (a % i === 0 && b % i === 0) return i;
  }
}
console.log(calculateGCD(72, 88)); // 8
```

####Process

1. 매개변수로 받은 a, b 중에 작은 수를 구해서 min변수에 저장한다
2. min을 1씩 마이너스하며 a, b값 모두의 나머지 값을 구한다
3. a, b 둘 다 나머지 값이 0이 되는 i값이 나올 때까지 2를 반복하고 0이 될 때에 i값을 리턴한다

### n개의 수의 최대 공약수를 구하는 함수

```js
function calculateGCD2(...num) {
  let min = Math.min(...num);
  for (let i = min; i > 0; i--) {
    let checker = num.every(v => v % i === 0);
    if (checker) return i;
  }
}
console.log(calculateGCD2(112, 72, 88));
// 8
```

#### Process

1. 매개변수로 받은 num중에서 최소값을 구해서 min변수에 저장한다
2. min을 1씩 마이너스하며 num에 있는 모든 수의 나머지값을 구한다
3. every함수를 사용하여 나머지 값이 모두 0이 될 때에만 true를 리턴하고 그 값은 cheker변수에 저장한다
4. checker가 true가 된 경우 즉, 모든 num에서 나머지 값이 0이 되었을 때 i값을 리턴한다