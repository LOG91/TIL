# React 기본강좌(ZeroCho TV)

### 4-1 React 조건문
#### false, undefined, null은 jsx에서 없음을 의미한다
리액트의 조건문은 3항 연산자를 많이 사용한다

jsx에서 if와 for은 쓸 수 없다

그래서 조건문으로 아래와 같은 표현이 가능하다!

counter가 0일 때는 아무 태그도 없게 하고 싶다면 아래와 같이 하면 된다!
```jsx
<div>{this.props.counter !==0 ? <div>hello</div> : null}</div>
```
이것이 가독성이 안 좋아보이면 아래와 같은 방법도 가능하긴 한데 개인적으로

가독성이 더 안 좋아 보인다
```jsx
renderHello = () => {
  return (this.props.counter !==0 ? <div>hello</div> : null)
}

render() {
  return (<div>{this.renderHello()}</div>)
}
```
#### setTimeout
반응속도체크 페이지를 만드는데 setTimeout을 사용했다

정말 오랜만에 setTimeout을 취소하는 clearTimeout을 보게 되었다

학원에서 js만 계속 공부할 때 많이 썼던 것이 생각이 났다

#### Webpack 설정 devtool
Webpack으로 번들링 후 디버깅을 하다보면 번들링이 된 상태로 코드의 에러 부분을

띄워주기 때문에 어디에서 어떤 문제인지 잡아내기가 어렵다

그때! 아래와 같이 설정에 넣어주면 내가 작성한 코드 그대로에서 에러 부분을 표시해준다!
```js
webpack.config.dev.js

{ devtoll: 'source-map' }
```