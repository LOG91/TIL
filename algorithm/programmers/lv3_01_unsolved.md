# 가장 긴 펠린드롬

앞뒤를 뒤집어도 똑같은 문자열을 팰린드롬(palindrome)이라고 합니다.
문자열 s가 주어질 때, s의 부분문자열(Substring)중 가장 긴 팰린드롬의 길이를 return 하는 solution 함수를 완성해 주세요.

예를들면, 문자열 s가 abcdcba이면 7을 return하고 abacde이면 3을 return합니다.

##### 제한사항

- 문자열 s의 길이 : 2500 이하의 자연수
- 문자열 s는 알파벳 소문자로만 구성

##### 입출력 예

| s       | answer |
| ------- | ------ |
| abcdcba | 7      |
| abacde  | 3      |

##### 입출력 예 설명

입출력 예 #1
4번째자리 'd'를 기준으로 문자열 s 전체가 팰린드롬이 되므로 7을 return합니다.

입출력 예 #2
2번째자리 'b'를 기준으로 aba가 팰린드롬이 되므로 3을 return합니다.



### My Solution (71.5점)

```js
function solution(s) {
  var answer = 0;
  for (let i = 0; i < s.length; i++) {
    let palindrome = compare(s, i);
    if (palindrome >= answer) answer = palindrome;
  }
  return answer * 2 + 1;
}

function compare(str, idx) {
  let answer = 0;

  function recursion(str, idx, i = 1) {
    if (!str[idx - i] || !str[idx + i]) return null;
    if (str[idx - i] === str[idx + i]) {
      answer++;
      recursion(str, idx, ++i);
    }
  }
  recursion(str, idx);
  return answer;
}

console.log(solution('abcdcba'));
```

71.5점이 왜 나오는지 궁금했었는데 abba와 같은 짝수의 펠린드롬을 검출하지 못하기 때문이었다

### Other Solution

```js
function solution(s){
  let {length} = s;
  while(length){
      for(let i = 0; i + length <= s.length; i++){
          if(isPalin(s.slice(i,i+length))) return length;
      }
      length--;
  }
}

function isPalin(s){
  for(let i = 0, {length} = s; i < length/2; i++){
      if(s[i] !== s[length-1-i]) return false
  }
  
  return true;
}
```



### Comment

- 내 사고가 많이 막혀있구나 라는 것을 느끼게 되었다 포기하지 않고 알고리즘 스터디는 계속해야 할 것 같다 너무 무리다 싶기 전까진...