## Binary Gap

Task description
A binary gap within a positive integer N is any maximal sequence of consecutive zeros that is surrounded by ones at both ends in the binary representation of N.

For example, number 9 has binary representation 1001 and contains a binary gap of length 2. The number 529 has binary representation 1000010001 and contains two binary gaps: one of length 4 and one of length 3. The number 20 has binary representation 10100 and contains one binary gap of length 1. The number 15 has binary representation 1111 and has no binary gaps.

Write a function:

function solution(N);

that, given a positive integer N, returns the length of its longest binary gap. The function should return 0 if N doesn't contain a binary gap.

For example, given N = 1041 the function should return 5, because N has binary representation 10000010001 and so its longest binary gap is of length 5.

Assume that:

N is an integer within the range [1..2,147,483,647].
Complexity:

expected worst-case time complexity is O(log(N));
expected worst-case space complexity is O(1).

### My solution

```js
// you can write to stdout for debugging purposes, e.g.
// console.log('this is a debug message');

function solution(N) {
  // write your code in JavaScript (Node.js 8.9.4)
  let gapArray = [];
  let count = 0;
  let flag = false;
  let maxGap = 0;
  while (N >= 1) {
    if (N % 2 === 0) {
      if (flag) count += 1;
    } else {
      flag = true;
      if (count > maxGap) maxGap = count;
      count = 0;
    }
    N = Math.floor(N / 2);
  }
  return maxGap;
}
```

### Second

```js
function solution(N) {
  // write your code in JavaScript (Node.js 8.9.4)
  const binary = N.toString(2);
  let countArray = 0;
  let count = 0;
  for (let v of binary) {
    if (+v) {
      if (count >= countArray) countArray = count;
      count = 0;
    }
    if (!+v) count++;
  }
  return countArray;
}
```

### Comment

Codility 에서는 처음 풀어 봤는데 사이트가 더 깔끔하고 풀이 관련 정보들도 많이 나오긴 한다  
근데 Best Practices 가 없는 것 같아서 아쉽다 ㅠㅠ  
**다시 알아보니 완전 성공이 아니고 20%의 버그가 발생했고 80%였다..!**
