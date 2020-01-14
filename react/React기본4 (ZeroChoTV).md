# React 기본강좌(ZeroCho Tv)

### 3-10 shouldComponentUpdate

리액트의 컴포넌트 중에 최적화하기에 적합한 함수다

ReactDevTools의 highlight기능으로 페이지의 동작을 보면 얼마나 동작 하나 하나에 관계없는

컴포넌트들이 얼마나 자주 렌더링이 되는 지 알 수 있다

**굉장히 좋은 익스텐션데스네🐶**

리액트 시작하고 최적화의 필요는 알았지만 늘 미뤄왔는데 이번에 제대로 배우게 되었다!

이 함수는 매개변수로 nextProps, nextState, nextContext를 받는다

```js
shouldComponentUpdate(nextProps, nextState, nextContext) {
  if(this.state.counter !== nextState.counter) {
    return true;
  }
  return false;
}
```

이 LifeCycle엔 반드시 리턴 값이 True Or false로 있어야 한다

true는 렌더링을 일어나게 하는 것이고 false는 안 일어나게 하는 것이다

위의 식을 보면 counter값이 같으면 렌더링 하지 않도록 하는 코드이다

#### nextContext!
여러 컴포넌트를 거치지 않고 변화가 일어나는 컴포넌트만 렌더링이 일어나게 해주려면

사용한다고 하고 말로만 듣던 ContextAPI라고 한다



### 3-11 PureComponent와 React.memo

앞서 배웠던 shouldComponentUpdate를 자동적으로 할 수 있도록 한 것이 PureComponent이다

그래서 컴포넌트 클래스의 extends를 Component가 아닌 PureComponent로 하면 된다

Hooks의 경우엔 lifeCycle 함수가 없기 때문에 React.memo 함수로 컴포넌트를 감싸주면 된다

```jsx
import React, { memo } from 'react';
const Hello = memo(() => {
  return <div>hello</div>
});
```

모든 부분에 Pure를 쓰면 될 것 같지만 간혹 일부러 렌더링을 막는 경우도 발생하기 때문에

그땐 일반 Component와 shouldComponentUpdate를 커스터마이징해서 쓴다고 한다

하지만 일반적인 경우엔 쓰는 것이 좋다 리팩토링 예약



### 3-12 React.createRef
CreatRef는 Class Component의 ref를 Hooks의 ref 와 비슷하게  
조금 더 간략하게 선언할 수 있는 방식이다
```jsx
inputRef;
<input ref={c=> this.inputRef(c)}/>
위와 같은 방법을 아래와 같이 바꿀 수 있다

import { createRef } from 'react';
input = createRef();
<input ref={this.input} />
```
하지만 무조건 createRef가 또 좋은 것은 아니다

class컴포넌트에서는 함수를 넣기 때문에 그 안에 다른 로직을 더 넣어줄 수 있기 때문이다

함수형은 늘 다른 것을 제공한다 (후후)

### 3-13 state와 props 연결하기
#### render 안에 setState를 넣어 무한 반복이 되게하는 실수는 이제 X
![alt text](https://upload.wikimedia.org/wikipedia/en/e/e0/Gollum.PNG)
##### 골룸 사진 너무 남발하지만 나름 최애;;;;;
#### props는 부모가 바꿔야 한다 자식이 바꾸는 것은 아니다
하지만 props를 바꿔야 하는 경우가 개발하다보면 생긴다고 한다

그땐 자식의 state에 부모의 props를 넣어줘서 바꾸도록 한다!