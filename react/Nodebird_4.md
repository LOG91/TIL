# Nodebird Project 4

우선 지금 내 상황을 먼저 알리자면 진행중이던 프로젝트에서 어떤 한 에러로

2일을 꼬박 스트레스 받으며 풀지 못한 후에 환기를 시키기 위해 이것으로 다시 돌아왔다

음.. 현업에 있어서는 꼭 문제를 해결해야 하니 상황이 다를 수 있겠지만 어느 정도에서 잠깐 환기를

시켜주고 재개하는 것은 어떤 영역에서나 어느 정도는 필요한 부분인 것 같다

깨달은 것은

- 다시 Nodebird를 하니 전보다 더 재밌다
- 마냥 프로젝트개발이 아니라 공부는 역시 필요하다 React dnd(2일 고생)도 문서를 다시 파보고 재개해야지...

### ES2015 generator

제너레이터는 존재는 알고 있었지만 괴이한 문법과 필요하지 않음으로 인하여 건드리지 않고 있었다

하지만 redux-saga를 할 때 필요하기 때문에 공부하게 되었다 (강의에 있음)

generator는 자바스크립트의 기본적인 로직 실행과 다르게 움직인다고 보면 된다

방법은 간단하다 아래와 같이 function 옆에 \*를 붙여주면 된다

```js
function* generator() {
  console.log(1);
  console.log(2);
}

const gen = generator();

gen.next(); // 1 2
// 리턴값: {value: undefined, done: true}
```

위와 같이 변수에 담아주고 next를 실행시에 안에 있던 로직이 실행된다

yield를 이용하면 더 멋진 일을 할 수 있다

```js
function* generator() {
  console.log(1);
  console.log(2);
  yield 'hello';
  console.log(3);
}

const gen = generator();

gen.next(); // 1 2
// 리턴값: {value: 'hello', done: false}

gen.next(); // 3
// 리턴값: {value: undefined, done: true}
```

yield는 중단점 역할을 하고 리턴값의 value로 내보내지게 된다

그리고 그 다음 next()실행 리턴값을 본다면 대략적으로 어떻게 제너레이터가 작동하는지를

알 수 있다

마지막 한 가지만 더 해보자면

```js
function* generator() {
  yield 1;
  yield 2;
  yield 3;
  yield 4;
}
function* generator() {
  yield* [1, 2, 3, 4];
}
```

위는 같은 결과를 가져온다 yield 뒤에 \*를 붙이면 iterable을 처리할 수 있다!

### takeLatest & takeEvery

둘은 거의 비슷한 기능을 수행하지만 takeLatest는 이전 요청이 끝나지 않은 것이 있으면

이전 요청을 취소한다

아래의 코드로 10번의 요청이 들어올 경우에 BYE_SAGA는 10번이 아닌 한 번만 호출된다

```js
function* watchHello() {
  yield takeLatest(HELLO_SAGA, function*() {
    yield delay(1000);
    yield put({ type: 'BYE_SAGA' });
  });
}
```
버튼을 막 클릭해서 서버로 10번의 로그인 요청이 간다고 하자

그때 SAGA에서 제어가 가능한 것이다

둘 중 하나를 고를 때는 둘 다 유효하게 쳐 줄 것인가 하나만 쳐 줄 것인가를 고민해보고

결정하면 된다!

### call & fork
call로 함수를 감싸주게 되면 이것은 동기적으로 실행하라는 것이고,

fork는 비동기적 실행을 말한다

예를 들어 loginAPI호출로 서버의 데이터를 받아야 하는 경우에는 call로 감싸줘서
`yield call(loginAPI)`이런 식으로 작성하면 된다


### LOGIN_REQUEST의 필요성
대부분의 앱에는 로그인 요청시를 포함한 잠깐의 대기 시간에 spinner를 준다

그때 LOGIN_REQUEST때 isLoading상태를 준다면 구현이 가능하다!

### try catch의 필요성
js코드에서 에러가 나면 서버가 죽어버리는 경우가 있다

하지만 try catch를 통하여 잡으면 서버가 죽지 않는다

### 굳이 saga를..?
나의 정말 궁금했던 부분이다 saga를 안 쓰고 메인 코드에서 비동기 처리를 해주면 되지 않나 싶었다

아래와 같이 말이다.
```js
useEffect(async()=> {
  dispatch({
    type: 'LOG_IN_REQUEST'
  });
  await axios.post('/login');
  dispatch({
    type: 'LOG_IN_SUCCESS'
  })
})
```
이렇게 해도 가능하다 하지만 이렇게 되면 로그인이 필요한 모든 코드에 작성을 해주는 중복이 일어난다

비동기 요청은 saga에서 전담을 시키는 것이라고 보면 된다

그것이 더 편하기 때문에!

그리고 테스트코드 작성에서도 saga를 쓰는 편이 훨씬 유리하다고 한다!

### UseEffect에 객체는 넣지 말기!
객체 비교는 어렵기 때문에 객체를 직접 넣지 말고 객체의 키값을 넣어주는 것이 좋다

### id값 달아주기
comment던지, user든지 고유id값으로 구분을 하기 때문에 id를 달아주는 것이 좋다

db쪽으로 넘어가면 고유 id Key가 생성되기 때문에 그것을 사용하면 된다

예를 들어 name === action.name 이렇게 가져오는 값이 없도록

id값 비교를 통해서 하면 된다 물론 filtering기능 같은 것에서는 비교가 필요하지만

웬만하면 안전하게 id값 비교를 통해서 가져오자!