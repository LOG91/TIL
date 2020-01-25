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

그때 배운 것들을 다 까먹은 것 같았지만 다시 보니 기억도 나고 할맛도 나네..ㅎㅎ

#### 변화는 일어나지만 렌더시키지 않고 싶은 것들은 state 외에 다른 변수로 선언!
반응 속도체크 예제에서 시간초 계산은 변하는 값이지만 state에 담을 필요는 없다

담게 되면 렌더링이 다시 일어나기 때문이다 ZeroCho님은 class의 this에 넣어주었다!

#### Webpack 설정 devtool
Webpack으로 번들링 후 디버깅을 하다보면 번들링이 된 상태로 코드의 에러 부분을

띄워주기 때문에 어디에서 어떤 문제인지 잡아내기가 어렵다

그때! 아래와 같이 설정에 넣어주면 내가 작성한 코드 그대로에서 에러 부분을 표시해준다!
```js
webpack.config.dev.js

{ devtoll: 'source-map' }
```

### 4-4 반응속도체크 Hooks로 전환하기
Hooks로 바꾸면서 class의 this를 이용해 선언했던 변수를 this를

이용할 수 없게 되었다 그때 그 대신 useRef를 이용해서 한다

Hooks에서 값이 바뀌어도 render를 호출하고 싶지 않은 변수들은 ref에 넣어서 사용한다

한 가지 주의할 점은 아래와 같이 접근할 때 current에 접근을 해야 한다!

```jsx
const ResponseCheck = () => {
  const timeout = useRef(null);
  const startTime = useRef();
  const endTime = useRef();


  const fn = () => {
   if(state === 'waiting') {
      startTime.current = new Date();
   } 
  }
}
```
#### return 내부에 if, for 쓰기
jsx의 {}에는 for와 if사용이 불가능하고 3항 연산자 밖에 쓸 수 없다

하지만 함수 안에는 for와 if를 쓸 수 있다는 방법과 즉시실행함수를 이용하면 아래와 같이 가능하다

하지만 만만치 않게 지저분하기 때문에 이렇게 할 바에 함수로 빼는 편이 낫다!
```jsx
return (
  <div>
    {(()=> {
      if(this.state.target.length>=0){
        return <div>hello</div>
      }else {
        return null;
      }
    })()}
  </div>
)
```

