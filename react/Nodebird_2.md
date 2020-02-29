# Nodebird Clone Project - 2

### 컴포넌트 분리

태그를 한 곳에 모아놓을 수록 리렌더링 시에 성능이 좋지 않다

컴포넌트로 나눠줄수록 성능 최적화에 좋다!

### &&의 사용
카드 컴포넌트를 렌더링해주는 코드의 일부다
```js
<Card
  key={c.createdAt}
  cover={c.img && <img alt="example" src={c.img} />}
  actions={[
    <Icon type="retweet" key="retweet" />,
    <Icon type="heart" key="heart" />,
    <Icon type="message" key="message" />,
    <Icon type="ellipsis" key="ellipsis" />
  ]}
  extra={<Button>팔로우</Button>}
>
```
cover쪽 코드를 보면 c.img가 존재할 경우에 넣어줄 값을 이야기하고 있다

&& 정말 많이 사용하는 코드인데 한동안 아예 사용하지 않고 있었다

이 코드를 보고 있을 때 넣어주면 되는 값들을 많이 처리해야함을 느낀다

### 배열 안에 JSX 문법
JSX문법을 배열 안에 넣는 경우엔 key를 꼭 넣어주도록 하자

리액트가 배열은 반복문이라고 판단하기 때문이다!