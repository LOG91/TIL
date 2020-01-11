# 출석부 Project 회고2

### 서버쪽 에러

여느때와 같이 console.log를 찍어가며 디버깅을 하고 있었다

이상한 것이 있었는데 console.log를 산재해 놔서 여러 부분이 찍혀야 하는데 어느 코드 이후부터는

찍히지 않는 것이었다 그렇다고 디버거에서 오류가 뜨는 것도 아니었다

그래서 코드를 한 줄씩 좁혀가는데 어떤 api통신 이후에는 console.log도 찍히지 않을 뿐더러

이후 코드 실행이 되지 않음을 발견했다



### api통신의 최소화

componentDidMount와 shouldComponentUpdate의 코드를 만지는 도중에 나의

큰 실수를 발견하게 되었다

![alt text](https://upload.wikimedia.org/wikipedia/en/e/e0/Gollum.PNG)

그것은!

currentSection이 현재 사람의 목록인데 페이지를 url이 바뀔 때마다 다시 api통신을 하여

데이터를 불러오고 state에 업데이트하는 것이었다

미리 데이터를 한 번만 불러와서 state에 두고 객체를 쓰던지 배열을 쓰던지 하면 통신하지 않고

state에서 꺼내오기만 하면 됐었는데 반복작업을 하고 있던 것이었다..!

전체 다 불러와도 충분한 크기의 데이터였음을 생각하면 큰 실수가 아니었나 싶다

하지만 이 생각마저 실수일 수 있겠지만 현재 내 판단은 통신을 줄이는 게 맞다는 것이었다

```js
shouldComponenetUpdate() {
  fetch(`api/sheet/${blahblah}`).then(res=>res.json()).then(res={
    this.setState({ sheet: res }))
}
}
```

이런 식의 코드를 짜고 있었다