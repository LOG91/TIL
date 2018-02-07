## Square Every Digit

```
Welcome. In this kata, you are asked to square every digit of a number.

For example, if we run 9119 through the function, 811181 will come out, 
because 92 is 81 and 12 is 1.

Note: The function accepts an integer and returns an integer
```

### My solution
```js
function squareDigits(num){
  //may the code be with you
  num = num.toString().split('');
  for(let i = 0; i < num.length; i++){
    num[i] = parseInt(num[i]);
    num[i] *= num[i];
  }
  return parseInt(num.join(''));
}
```

### Best practices
```js
function squareDigits(num){
  return Number(('' + num).split('').map(function (val) { return val * val;}).join(''));
  
}
```

### Needs
- Array.prototype.map

### Comment
새로운 함수를 배우는데엔 게으른 내 자신을 본다 ㅠ.ㅠ