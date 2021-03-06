# 181217 TIL (Velopert React Tutorial)

## 프론트엔드 프레임워크 리액트

자바스크립트를 이용한 동적 페이지 기능이 많아 지고 관리해줘야 할 데이터의 양도 많아지면서 라이브러리와 프레임워크가 개발자에게 꼭 필요하게 되었다
리액트도 그 중 하나인 라이브러리다

다들 프레임워크로 생각을 많이 하지만 공식 홈페이지에도
라이브러리로 소개가 되어 있다
그리고 유명한 라이브러리 3대장 Angular, React, Vue가 있는데
각자 추구하는 방향이 조금씩 다르다고 한다
그래서 좋은 개발자라면 무조건 하나의 프레임워크만을 고집하는 것이 아니라 필요한 곳에 필요한 프레임워크를 배치할 수 있다고 한다

**리액트는 컴포넌트 위주의 라이브러리라고 한다!**

### 자유도가 높은 리액트

리액트는 자유도가 높은 라이브러리라고 한다
그래서 예를 들어 상태관리와 HTTP에도 각각 다른 라이브러리를
불러와서 쓸 수 있다 어떤 개발자에게는 이것이 불편함이 된다고는 하지만 실력이 있는 개발자는 이 점을 굉장히 좋게 여긴다고 한다
내가 커스터마이징을 해가며 다이나믹하게 애플리케이션을 구성할 수 있기 때문이라고 한다

### 데이터를 담당하는 props, state

#### props

props를 사용해서 부모로부터 데이터를 전달받을 수 있다

```js
// App.js
render(){
  return <Whale name="log91">
}

// Whale.js
  return render(){
    <div>{안녕하세요 제 이름은 this.props.name}</div>
  }
```

### 리액트 튜토리얼 (from Velopert블로그)

### 컴포넌트 만들기

컴포넌트는 class를 이용해서 만드는 방법과 함수를 이용해서 만드는
두 가지 방법이 있다

#### 1. class 컴포넌트

```js
import React, { Component } from "react";

class App extends Component {}
```

#### 2. 함수형 컴포넌트

단순히 props만 받아와 작성하는 컴포넌트의 경우엔 아래와 같이
더 간단하게 작성할 수 있다
state와 lifeCycle이 빠지게 된다
이것의 유무는 미세한 성능의 차이가 있다고 하는데 거의 차이가 안난다고
보면 된다고 한다

```js
const MyName = ({ name }) => {
  return <div>안녕하세요! 제 이름은 {name} 입니다.</div>;
};
```

#### 동적인 데이터를 다루는 state
state는 리액트의 핵심적인 기능 중 하나다
이를 통하여 동적으로 변하는 데이터를 관리한다
```js
class ABC extends Component {
  state{
    number: 0;
  }
}
```
위와 같이 class field를 통하여 사용할 수 있다
class field를 사용하지 않으면 아래와 같이 작성해야 한다
```js
class ABC extends Component {
  constructor(props){
    super(props);
    this.state = {
      number=0;
    }
  }
}
```
#### setState
우리가 state를 통해 데이터를 다룰 때 꼭 지켜줘야 하는 부분은
setState를 통해서 변화를 시켜줘야 한다는 것이다
```js
const {number} = this.state
this.setState({number:number+1})
```
위와 같이 해줄 수 있다