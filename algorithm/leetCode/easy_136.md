## 136. Single Number

Given a **non-empty** array of integers, every element appears *twice* except for one. Find that single one.

**Note:**

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

### My Solution

1번째 방법

```js
var singleNumber = function (nums) {
  return nums.reduce((ac, cv) => ac ^ cv);
};

```

2번째 방법

```js
var singleNumber = function (nums) {
  const obj = nums.reduce((ac, cv) => {
    if (ac[cv]) ac[cv] = 2;
    else {
      ac[cv] = 1;
    }
    return ac;
  }, {})
  for (value in obj) {
    if (obj[value] === 1) return value;
  }
};
```

### Best Practices

```js
var singleNumber = function(nums) {
    let length = nums.length;

    if(length < 2) return nums[0];

    let result = 0;

    for(let i = 0; i < length; i++) {
        result ^= nums[i];
    }
    
    return result;
};
```

최고 스펙으로 나온 풀이가 이것이긴 한데 비슷하게 해봤는데 나는 그 스펙이 나오지 않아서 똑같이 복사해서 다시 실행해 봤는데 최고로 안나온다

LeetCode의 채점에 문제가 있는건지.. 잘 모르겠다.!!



### Comment

- 사실 이 문제는 코딜리티에서 풀었던 똑같은 것이라 비트연산자를 바로 이용해서 풀 수 있는 문제였다
- 그래서 아쉬운 마음에 두번째 방법을 추가했고 더 좋은 효율을 위해 세번째를 생각하려다가 다른 것이나 하기로 했다