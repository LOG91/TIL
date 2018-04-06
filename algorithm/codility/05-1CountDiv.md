## CountDiv
Write a function:

function solution(A, B, K);

that, given three integers A, B and K, returns the number of integers within the range [A..B] that are divisible by K, i.e.:

{ i : A ≤ i ≤ B, i mod K = 0 }

For example, for A = 6, B = 11 and K = 2, your function should return 3, because there are three numbers divisible by 2 within the range [6..11], namely 6, 8 and 10.

Assume that:

A and B are integers within the range [0..2,000,000,000];
K is an integer within the range [1..2,000,000,000];
A ≤ B.
Complexity:

expected worst-case time complexity is O(1);
expected worst-case space complexity is O(1).

### My solution
```js
function solution(A, B, K) {
    // write your code in JavaScript (Node.js 8.9.4)
    let result = Math.floor(B/K) -Math.floor(A/K);
    return A % K === 0 ? result+1 : result;
}
```

### Comment
잔뜩 긴장하고 시작했지만 종이에 끄적이다가 의외로 빨리 패턴을 발견할 수 있어서  
비교적 짧은 시간에 풀 수 있었다