## 461. HammingDistance

The [Hamming distance](https://en.wikipedia.org/wiki/Hamming_distance) between two integers is the number of positions at which the corresponding bits are different.

Given two integers `x` and `y`, calculate the Hamming distance.

**Note:**
0 ≤ `x`, `y` < 231.

**Example:**

```js
Input: x = 1, y = 4

Output: 2

Explanation:
1   (0 0 0 1)
4   (0 1 0 0)
       ↑   ↑

The above arrows point to positions where the corresponding bits are different.
```

### My Solution

```js
var hammingDistance = function (x, y) {
  let xb = binary(x);
  let yb = binary(y);
  if (xb.length > yb.length) {
    yb = [...Array(xb.length - yb.length)].fill(0).concat(yb);
  } else {
    xb = [...Array(yb.length - xb.length)].fill(0).concat(xb);
  }
  const diff = xb.reduce((ac, cv, idx) => {
    if (cv !== yb[idx]) ac++;
    return ac;
  }, 0)
  return diff;

  function binary(n) {
    arr = [];
    for (n; n >= 1;) {
      arr.unshift(n % 2);
      n = Math.floor(n / 2);
    }
    return arr;
  }
};
hammingDistance(3, 1);
```

### Comment

코딜리티가 난이도가 어려워져 학원에서 알고리즘 스터디가 암묵적으로 중단되었었는데 분위기를 환기시킬 목적으로 LeetCode로 진행하기로 했다

그래서 난이도도 일단 easy로 가기로 했는데 easy라서 그런지 재미있게 풀었다

LeetCode는 내가 푼 알고리즘의 런타임을 다른 사람들과 비교하여 그래프로 보여주는데 나는 꽤 높은 런타임을 기록했다….

나의 알고리즘을 성장시킬 기회가 다시 찾아올 것 같아서 좋다 알고리즘 스터디를 할 것이 너무 기대된다 ^^