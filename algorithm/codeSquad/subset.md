## Subset
부분집합을 나열하는 알고리즘을 구하기

### My solution
```js
function part(arr, checker = arr[0][0], count = 0, result = []) {
  for (let i = 0; i < arr.length; i++) {
    result.push(arr[i]);
    result.push(arr[i].filter(v => v !== checker));
  }
  count++;
  if (count < arr[0].length) {
    part(result, arr[0][count], count);
  } else {
    console.log(result);
  }
}

part([
  ['a', 'b', 'c']
]);
```

### Comment
힌트를 보기 전에는 어떻게 접근해야 할지 엄두가 안났었다
아직 사고하는 것이 익숙하지 못한 것 같다
알고리즘은 정말 꾸준히 해야겠다..