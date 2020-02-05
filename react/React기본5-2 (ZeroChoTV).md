# React기본 (ZeroChoTV)
### 5-1 리액트 라이프사이클 소개
#### ComponentDidMount
컴포넌트를 DOM에 붙여줄 때 한 번 실행되는 함수다

Render가 처음 실행된 직후에 실행된다

setState로 인한 리렌더링이 일어날 때는 실행되지 않는다

#### ComponentWillUnmount
컴포넌트가 제거되기 직전에 실행된다

보통 ComponentDidMount와 짝을 이룬다

시작할 때와 끝날 때에 실행할 함수를 각각에 넣어주면 된다!

#### ComponentDidUpdate
리렌더링 될 때에 실행되는 라이프사이클이다

#### 컴포넌트의 일생 (Class의 경우)
constructor -> render -> ref등록? -> componentDidMount

-> (state,props변화시 -> shouldComponentUpdate(true) -> render -> componentDidUpdate)

-> (부모가 나를 없앨 때 -> componentWillUnmount -> 소멸

- shouldComponentUpdate에서의 분기 처리에 따라서 render가 될지 안 될지가 결정난다!

### 5-2 setInterval과 라이프 사이클 연동하기
setIneterval로 비동기 요청을 등록해놓는다면 willUnmount에서 취소해주는 것이 좋다

그렇게 하지 않을 때 컴포넌트가 사라져도 돌아가고, 새로 추가되면 또 다른 setInterval이 등록된다

아래와 같다!
```js
interval;

componentDidMount() {
  this.interval = setInterval(()=>{}, 1000)
}
componentWillUnmount() {
  clearInterval(this.interval);
}
```

### 5-4 고차 함수

### 5-6 class와 Hooks의 라이프사이클 비교
class에서는 componentDidUpdate, componentDidMount, componentWillUnmount를 선언하고

그 안에 동작 시에 일어나는 로직을 적으면 된다

하지만 Hooks에서는 state마다 useEffect를 등록해줘서 세 가지의 일을 모두 정의하는 방식으로 한다