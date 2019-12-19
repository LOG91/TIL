## 191216-17 TIL

### 리액트 공부 시작

리액트를 하긴 해도 너무 모르고 한다는 느낌이 강해서 강의를 검색해보았는데 ZeroCho 조현영님의

강의가 딱 좋아보였고 유튜브 강의와 인프런 유료 강좌를 들으며 공부하기로 결정했다

### ZeroCho TV 리액트 기본 강좌

#### 1-1 리액트를 왜 쓰는가?

- 사용자 경험이 좋아진다 앱과 같은 UX를 제공하게 된다

- 데이터와 랜더링 동기화에 좋다, 대규모 웹페이지에서 데이터와 화면을 동기화시키는 것에는 큰 어려움이 따른다

- 컴포넌트화, 중복을 제거한다

#### 1-3 HTML 속성과 상태(state)

state는 바뀌는 부분이다! 라고 생각하면 된다

state에 따른 렌더링이 놀랍지 않은 이유는 jQuery나 Vanilla로만 개발을 해보지 않아서일 것이다

대규모 서비스에서 이것이 얼마나 힘을 발휘하는지는 나중에 jQuery와 React 둘 다 해보면 알 수 있다

해볼 날이 있을까 ㅠ.ㅠ

#### 1-4 JSX와 바벨(babel)

원래 ZeroCho TV를 따라하면서 만든 코드다

리액트를 배우면서 내부가 어떻게 동작하는지 처음부터 만들어 본 적은 없는데 이렇게 만들어보니

JSX가 왜 생기게 된건지, JSX내부에서는 이렇게 동작하는 건지를 알 수 있었다

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <script src="https://unpkg.com/react@16/umd/react.development.js"></script>
  <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
  <title>Document</title>
</head>
<body>
  <div id="root">Hello HTML!</div>
  <script>
    const e = React.createElement;
    console.log(e);

    class LikeButton extends React.Component {
      constructor (props) {
        super(props);
        this.state = { liked: false };
      }
      render () {
        return e('button',
        {
          onClick: () => {
            this.setState({ liked: true });
            console.log('hello world!')},
            type: 'submit'
        },
        this.state.liked === true ? 'liked' : 'like');
      }
    }
  </script>
  <script>
    ReactDOM.render(e(LikeButton), document.querySelector('#root'));
  </script>
</body>
</html>

```

##### JSX

JSX는 js + xml이다

```js
return e('button',
        {
          onClick: () => {
            this.setState({ liked: true });
            console.log('hello world!')},
            type: 'submit'
        },
        this.state.liked === true ? 'liked' : 'like');
      }
      
return <button type="submit"
                onClick: () => {
                this.setState({ liked: true });
                console.log('hello world!')},
        }>{this.state.liked === true ? 'liked' : 'like'}</button>
```

원래는 js문법인데 태그가 들어가서 js스럽게 느끼지 않고 있었는데 사실 이것은 js였다!

babel이 아래에 있는 JSX문법을 createElement로 바꿔주는 것이다!

#### 1-8 Fragment와 기타 팁들

JSX에서 wrap해주는 태그가 없이 형제태그끼리 있게 되면 문법 오류가 난다

```html
//error
<div>1</div>
<div>2</div>

// ok
<div>
  <div>1</div>
  <div>2</div>
</div>
```

#### 1-9 함수형 setState

setState는 객체만 이용해서 하는 것이라 생각했는데 함수로도 가능하다!

prevState 즉 이전의 state값을 사용해야 할 경우에 한다고 한다

```js
setState({
  answer: this.state.value
});

setState((prevState) => {
  return { answer: prevState.value}
})
```

위와 같이 가능하다 함수형이 필요없이 위에 구문으로 해도 가능한 경우도 많지만

setState가 비동기로 동작하기 때문에 여러번 setState가 일어날 때 값의 참조가 잘못되는 경우가

있다 그때 사용해야 한다 나도 예전에 그런 경우가 있어서 어떻게 대처를 하긴 했었는데 기억이..

무튼 이 사용 방법도 자주 사용한다고 하니 알아두자!



#### 1-10 ref

리액트에서 document.querySelector는 거의 안 쓰는 것으로 알면 된다고 한다...

바닐라를 오래 했기 때문에 습관적으로 나오는 것은 document였는데...

리액트를 믿고 우리는 데이터 조작만 한다고 생각하면 된다고 한다!



##### ☝️tip

this.setState할 때 리렌더링이 일어난다는 사실을 잘 알아두자!

간단한 페이지는 상관 없지만 10초가 걸리는 작업이 input의 onChange가 일어날 때마다 일어난다고

생각하면 서비스는 불가하다

성능 최적화에서 기본적으로 알아야 하는 개념이다!

render 부분은 리렌더링 할 때마다 실행이 되는데 그 부분에 많은 로직을 담고 있다면

그 로직이 다시 재실행되다는 점을 알고 익명함수 등을 줄이도록 하자