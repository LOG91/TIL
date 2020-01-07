# React 기본강좌 (ZeroChoTV)

### 3-1 import require 비교

리액트에서 import가 사실 필요하지 않지만 많은 코드들이 import를 쓰고 있다

그렇다! 지금껏 import만 사용해왔고 require은 백엔드에서 쓰는 코드라며 사용하지 않고

둘의 차이점을 제대로 분간도 못했었다

하지만 지금 내가 강좌를 듣는 데서는 다 프론트엔드코드지만 require만 사용하고 있었다



#### require

노드의 모듈 시스템이다



### 3-2 리액트 반복문 (map)

#### defaultValue

리액트에선 input의 value와 onChange를 꼭 같이 넣도록 한다

그렇게 하지 않을 경우에는 defaultValue를 설정해줘야 한다

### 3-3 리액트 반복문 (Key)

```jsx
<ul>
  [{fruit: 'apple', taste: '맛있다'}, {fruit: 'banana', '달다'}].map((v, i) => {
return (
	<li key={v.fruit+v.taste}>{v.fruit}</li>
)    
  })
</ul>
```

key는 고유한 값을 넣어주면 되기에 정해진 것은 없다 +연산자로 여러 값을 더해줘도 된다!

하지만 map의 두번째 파라미터인 index는 넣지 않는 것이 최적화에 좋다고 한다

key={index}는 최악이고 key={value+index}도 권장되지는 않다고 하는데

이유는 아직 모르겠다 (찾아보기)



### 3-4 컴포넌트 분리와 props

코드를 짜다가 코드가 길어지고 반복이 될 경우엔 컴포넌트로 분리하는 것이 좋다

최적화에도 그것이 더 좋음!

**분리 방법!**

- 한 파일에 코드를 쭉 작성한다
- 반복이 생기는 부분을 컴포넌트로 분리한다!

이것을 `탑다운 방식`이라고 할 수 있다

큰 컴포넌트를 먼저 만들고 필요가 생길 때 분리를 진행하는 것이다

리액트 초보에게 권장되는 방식이다 반대로 `바텀업 방식`은 작은 단위를 먼저 만들고 조립을

해 나가는 방식인데 이것은 리액트에 숙달된 사람들이 하기 쉬운 방식이다!



### 3-5 주석과 메서드 바인딩

```jsx
import React from 'react';

class BaseBall extends React.Component {
  onChangeDiv = () => {
    
  }
  render() {
    return (
      <>
      	<div>BaseBall Game</div>
      	<input onChange={onChangeDiv}/>
      </>
    )
  }
}
```

위 코드에서 render함수를 제외하고는 모두 화살표 함수로 써줘야 한다

표현식으로 사용하기 위해서는 아래와 같은 처리를 해줘야 한다

```js
constructor(props) {
  super(props);
}
this.onChangeDiv = this.onChangeDiv.bind(this);
```

