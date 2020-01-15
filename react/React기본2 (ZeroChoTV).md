# ZeroChoTV 리액트 기본 강좌 2-1 ~

### 기본 강좌 1-2. React Hooks 사용하기

컴포넌트 개발에 Class를 사용하는 것보다 Function을 사용하고 싶은데 그렇게 하면 setState나 ref

사용이 불가능하다 사용자는 function에도 사용이 가능하도록 요구를 했고 그렇게 해서

개발된 것은 Hooks이다!



Class에서는 render만 재실행되지만 Hooks에서는 전체 함수가 재실행된다



리액트에서 못쓰는 속성 class와 for

```html
<div class="">hello</div>
<label for=""></label>

<div className="">hello</div>
<label htmlFor=""></label>
```

자바스크립트 코드이기 때문에 해석에서 어느 코드인지 분간이 어렵다

그래서 각각 className과 htmlFor로 바꿔줘야 한다!



### 기본강좌 2-3. Webpack으로 빌드하기

Node는 JS 실행기다!

리액트를 할 때 노드를 알아야 한다는 것은 서버를 알아야한다는 것이 아니라 JS 실행기를 알아야 한다는 것이다 아직 무슨 뜻인지 잘...

#### npm i -D

```
npm i -D webpack webpack-cli
```

웹팩을 설치했다

-D는 개발할 때만 쓰일 것이라는 뜻이다

실제 개발할 때 웹팩이 쓰이지 않는다고 한다 무슨 뜻인지 아직...

### 기본강좌 2-4. 모듈 시스템과 웹팩 설정

모듈 시스템이 생기면서 필요한 파일만 불러올 수 있게 되었다



```
npm i -D @babel/core // 바벨의 기본적인 것들 들어 있음
npm i -D @babel/preset-env // 우리의 브라우저에 맞게 바꿔준다
npm i -D @babel/preset-react // 리액트 해석 jsx도 이것을 통해!
npm i -D babel-loader // 바벨와 웹팩을 연결해준다
```



```js
const path = require('path');

module.exports = {
  mode: 'development',
  devtool: 'eval',
  
  // 1
  entry: {
    app: './client'
  },
  
  // 2
  module: {
    rules: [{
      test: /.\jsx?$/,
      loader: 'babel-loader',
      options: {
        presets: ['@babel/preset-env', '@babel/preset-react']
      }
    }],
  },
  
  // 3
  output: {
    filename: 'app.js',
    path: path.join(__dirname, 'dist')
  }
}
```

기초적인 리액트용 웹팩설정인데 이 순서를 생각해보면 좋다

entry (1) 에서 시작을 하고 moduling (2) 을 거쳐서 output (3)을 뽑아낸다!

웹팩 전체는 다섯가지를 기억하면 된다

- entry
- output
- loaders(module)
- plugins
- mode

이미 여기에 있는 것을 거의 다 배우고 있다 웹팩이 어려워보이지만 쪼개어 보면 크게 어려운 것이

아니다 겁먹지 말고 하나하나 접근하다보면 금방 배울 수 있을 것이다!



#### ☝️ babel-preset-env의 중요성

우선 `preset` 이란 plugin의 모음이라고 생각하면 된다

그렇기 때문에 방대한 양을 가지고 있고 추가로 설정해주는 방법이 존재한다

```js
module: {
    rules: [{
      test: /.\jsx?$/,
      loader: 'babel-loader',
      options: {
        presets: ['@babel/preset-env', '@babel/preset-react']
      }
    }],
  },
```

module의 options에 들어가는 이 설정이 중요하다!

이것은 어떤 브라우저든지 동작할 수 있도록 바벨이 최신 문법을 바꿔주는 설정인데

여기에 명시적으로 지원하고자 하는 브라우저만 기록을 할 수 있다

그냥 안 하면 모든 브라우저에 적용이 가능하지만 그렇게 되면 코드량이 많아질 수 밖에 없고

바벨 처리시간이 오래걸릴 수 밖에 없다

아래와 같이 설정이 가능하다 최신 크롬 버전 2가지까지 가능하도록

```js
options: {
        presets: [
        ['@babel/preset-env', {
          targets: {
            browsers: ['>5% in KR', 'last 2 chrome versions']
          }
        }],
          , '@babel/preset-react']
      }
```

##### 웹 사이트 browserslist를 참고하면 된다!

### 2-9 Webpack-dev-server와 hot-loader

Webpack-dev-server는 그동안 코드를 수정하면 다시 build하고 랜더링하는 반복적인 과정을

없애주는 라이브러리다

속성으로 hot을 지정해줄 수 있어서 실시간으로 소스코드 변경이 일어나면 변경된 모듈만 새로

번들링을 하고 변경된 모듈 정보를 브라우저에 전송한다

그때 브라우저는 변경을 인식하고 새로고침이 된다

#### WDS 장점

- 디스크에 저장되지 않는 메모리 컴파일을 사용하기 때문에 컴파일 속도가 빠르다



### Reference

- Velog [adam2](https://velog.io/@adam2) 님의 글

