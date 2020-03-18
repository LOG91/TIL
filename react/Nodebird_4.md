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

방법은 간단하다 아래와 같이 function 옆에 *를 붙여주면 된다
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
  yield* [1, 2, 3, 4]
}
```
위는 같은 결과를 가져온다 yield 뒤에 *를 붙이면 iterable을 처리할 수 있다!