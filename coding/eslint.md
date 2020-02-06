# ESlint 사용해보기
코딩 중 문득 생각이 들었다

내 코드가 과연...? 괜찮을 모양새를 갖고 있을까?

그래서 잠시 접어놓았던 코딩 컨벤션을 신경쓰기로 마음먹었다

귀찮아서 미뤄두는 습관을 져버리고 생각났을 때 바로 실행했다🐶

### Getting Started
```
npm install eslint --save-dev

npx eslint --init
```
위와 같이 입력하면 초기 설정을 하는 몇몇 절차가 terminal에 뜬다

완료되면 .eslintrc.js 파일이 생성되며 초기설정이 들어가 있다

이제 IDE쪽만 만져주면 된다 VSCode의 extension에서

eslint를 설치해주고 enable만 시켜주면 된다!

### airbnb base
물론 코딩컨벤션은 자유다

하지만 Best Practices와 같이 미리 개발팀에서 사용하는 좋은 예들이 있다

나의 경우는 많이 사용하는 airbnb의 컨벤션을 사용해보고 싶어서

컨벤션파일을 설치 후에 적용시켰고 당분간은 이걸로 해볼 예정이다!

### Plugin
EcmaScript 뿐만 아니라 HTML도 가능하다

```
npm i --save-dev eslint-plugin-html
```
후 eslintrc.js 파일에 아래와 같이 입력해주면 된다!
```js
plugin: [
  'html'
]
```