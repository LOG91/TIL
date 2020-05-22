# Webpack - Offiical Page
웹팩은 자바스크립트 모듈 번들러다

js파일 뿐만 아니라 html, css, jpg, png, font 모든 파일을 js파일 한 개로 묶는다

자바스크립트는 모듈을 만들기 위해서는 원래 IIFE를 이용하여야 한다

웹팩은 이 과정을 처리하고, 파일을 한 파일로 만들어 네트워크 통신을 최소화하여 페이지의 성능을 높인다

### 웹팩의 주요 네 가지 개념
엔트리, 아웃풋, 로더, 플러그인
#### 엔트리
의존성 그래프의 시작점을 엔트리라고 한다

웹팩은 엔트리를 통하여서 모듈을 로딩하고, 하나의 파일로 묶는다
#### 아웃풋
엔트리를 통하여 하나가 된 파일이 저장되는 장소다

주로 루트 폴더에 dist폴더를 생성하여 그 안에 많이 넣는다

폴더 이름과 파일이름을 직접 지정해줄 수 있다

#### 로더
웹팩은 자바스크립트 밖에 모르는 녀석이다

하지만 앞서 css, jpg, png, font 모두 해당된다고 말했다

로더가 이때 필요하다 비 자바스크립트 파일을 자바스크립트로 알아들을 수 있게 해석해주는 도구다

로더는 test와 use 키로 구성된 객체로 설정한다

대표적인 두 로더의 사용방법을 통해 알아보자

##### babel-loader
ES6에서 ES5로 변환하는데 바벨을 사용해야 한다

```js
module.exports = {
  module: {
    rules: [{
      test: /\.js$/,
      exclude: 'node_modules',
      use: {
        loader: 'babel-loader',
        options: {
          presets: ['env']
        }
      }
    }]
  }
}
```
test에 자바스크립트 확장자를 갖는 파일을 정규표현식으로 지정했다

node_moudles 폴더는 패키지 폴더이므로 제외하기 위해서 exclude에 설정한다

use에 로더를 설정하는데 babel-loader 를 추가했다

loader는 웹팩 패키지에 디폴트로 들어가 있는 것이 아니라서 개별 설치를 해줘야 한다

위의 경우엔
```
npm i --save-dev babel-loader babel-core babel-preset-env
```

##### style-loader, css-loader
css로더는 css파일을 js가 해석할 수 있도록 수정해주는 역할

style로더는 자바스크립트로 변환된 스타일시트를 동적으로 DOM에 추가하는 로더다

둘 다 필요한 역할이 있기 때문에 둘은 같이 쓰인다

```js
module.exports = {
  module: {
    rules: [{
      test: /\.css$/,
      use: ['style-loader', 'css-loader']
    }]
  }
};
```

#### 플러그인
웹팩에서 알아야할 마지막 개념이 플러그인이다

로더가 파일단위로 처리하는 반면 플러그인은 번들된 결과물을 처리한다

번들된 자바스크립트를 난독화 한다거나 특정 텍스트를 추출하는 용도로 사용할 수 있다

##### UglifyJsPlugin은 로더로 처리된 자바스크립트 결과물을 난독화 처리하는 플러그인이다

UglifyJsPlugin은 로더로 처리된 자바스크립트 결과물을 난독화 처리하는 플러그인이다

플러그인을 사용할 때는 웹팩 설정 객체의 plugins 배열에 추가한다

```js
const webpack = require('webpack')

module.exports = {
  plugins: [
    new webpack.optimize.UglifyJsPlugin(),
  ]
}
```



## Reference
- http://jeonghwan-kim.github.io/ (김정환 블로그)