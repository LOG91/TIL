## Great Common Divisor (최대공약수 구하기)

최대공약수가 무엇인지 알아본다.
패턴을 찾고 이를 내가 알고있는 자바스크립트 문법만으로 풀어본다. 
최대공약수를 쉽게 구하는 공개된 공식이 있을 수 있지만, 
본인이 알고 있는 반복문과 함수를 사용해서 풀어보도록 한다.

### My solution
```js
// 공약수 구하는 함수
function commonDivisor(num) {
  let result = [];
  for (let i = 0; i <= num; i++) {
    if (num % i === 0) result.push(i);

  }
  return result;
}

// 최대 공약수를 구하는 함수 (중첩 for문 사용)
function greatCdUsedFor(num1, num2) {
  let num1CD = commonDivisor(num1);
  let num2CD = commonDivisor(num2);
  let result = [];
  for (let i = 0, len1 = num1CD.length; i < len1; i++) {
    for (let j = 0, len2 = num2CD.length; j < len2; j++) {
      if (num1CD[i] === num2CD[j]) result.push(num1CD[i]);
    }
  }
  return result[result.length - 1];

}

// 최대 공약수를 구하는 함수 (filter 사용)
function greatCdUsedFilter(num1, num2) {
  let num1CD = commonDivisor(num1);
  let num2CD = commonDivisor(num2);

  var result = num1CD.filter(function (n) {
    return num2CD.indexOf(n) > -1;
  });
  return result[result.length - 1];
}
```

### Comment
- 공약수가 무엇인지 다시 검색해봤음..
- 손으로 써가면서 패턴을 파악하는 것이 즐겁긴 하나 겨우 방법을 찾아서 푼 것이고
연습이 굉장히 많이 필요할 것 같다

### Needs
- filter함수 등 Iterator 함수에 익숙해지는 것