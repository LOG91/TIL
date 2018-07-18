# 180718 TIL

### 카카오 알고리즘 난이도(하) Review

```js
function kakao(arr1, arr2) {
  let vinary1 = arr1.map((v) => v.toString(2));
  let vinary2 = arr2.map((v) => v.toString(2));
  let sum = vinary1.map((v, i) => Number(v) + Number(vinary2[i]));
  let result = sum.map(v => {
    return v.toString().replace(/1|2/g, '#').replace(/0/g, ' ');
  })
  return result;
}

console.log(kakao([46, 33, 33, 22, 31, 50], [27, 56, 19, 14, 14, 10]));
```

#### 리뷰

- 반복문(map)이 많다
- replace를 한 번에 할 수 있다
- 두 array를 binary를 만드는 방식을 두 array의 OR연산자를 사용하는 방법으로 바꿀 수 있다

#### 반복문 없애기

```js
function kakao(arr1, arr2) {
  let result = arr1.map((v, i) => {
    let sum = Number(v.toString(2)) + Number(arr2[i].toString(2));
    return sum.toString().replace(/1|2/g, '#').replace(/0/g, ' ');
  });
  return result;
}

console.log(kakao([46, 33, 33, 22, 31, 50], [27, 56, 19, 14, 14, 10]));
```

총 4번의 map함수가 있었는데 1개로 줄일 수 있다 물론 가독성이 조금 떨어질 수 있다

#### replace 줄이기

```js
sum.toString().replace(/1|2/g, '#').replace(/0/g, ' ');
->
return sum.toString().replace(/0|1|2/gi, (match) => (match === '1' || match === '2') ? '#' : ' ')
```

두번째 인자로 함수를 넣으면 첫번째 인자값에 매치된 string값이 할당된다

그것에 조건문을 넣으면 위와 같이 이용할 수 있다

#### or연산자 이용

```js
const decode = (n, arr1, arr2)=> {
  const result = []
  for(let i =0; i<n; i++){
    let wall =  arr1[i] | arr2[i]
    wall = wall.toString(2).replace((/0|1/gi), (match)=> match==='1' ? '#' : ' ')
    result.push(wall)
  }
  return result;
}
```

알고리즘 스터디 다른 분 코드인데 |연산자를 이용해 계산한 것을 알 수 있다

우리가 5로 쓸 뿐이지 컴퓨터는 모든 문자는 binary로 받아들인다 때문에 어느 문자열이라도

toString(n)으로 변환할 수 있고 두 문자열을 비트연산할 때에 toString(n)을 먼저 사용하지 않더라도 12 | 41 이런 식으로 가능하다