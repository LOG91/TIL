# React기본 (ZeroChoTV)
### 리액트 라이프사이클 소개
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