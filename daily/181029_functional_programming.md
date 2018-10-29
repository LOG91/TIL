# 181029 TIL (OfflineLesson)

### Event 이해

stopPropagation

mouseover이벤트를 발생시킬 때에도 사용자의 의도를 파악해서 UX를 짜야 한다
(EX) 소분류 레이어에서 hover 각도

좋은 UI개발자라면 UX를 생각하며 이벤트를 구현할 수 있어야 한다

### first-class-function

함수는 그저 하나의 값이다

인자로 쓰일 수도 있고 반환될 수도 있다

배열의 원소나 객체의 속성으로도 물론 사용될 수 있다

### currying

```js
function add(a,b){
    return a+b;
}
add10 = add.bind(undefined, 10);
add10(20); // 30
```

bind함수는 currying으로 동작한다

#### 간단한 curry 함수

```js
curry = f => a => b =>f(a,b)
```

### FP 철학과 이해

FP : functional programming

#### FP 키워드

- Higher-order-function
- stateless
- immutability
- Referential transparency (참조투명성, 순수성)

map, reduce 등 새로운 배열을 반환하는 FP의 대표적 함수

#### 비동기도 Stream으로

```js
var stopStream = Rx.Observable.fromEvent(document.querySelector('button'), 'click');
input.takeUntil(stopStream)
  .map(event => event.target.value)
  .subscribe(value => console.log(value)); // "hello" (click)
```

#### Immutabliity

직접 현재의 상태를 바꾸지 않는 방법이다

Undo 기능은 대표적으로 immutability가 필요한 기능이다

git commit도 마찬가지다

