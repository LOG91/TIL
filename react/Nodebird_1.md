# Nodebird Clone Project - 1
프로젝트는 ZeroCho님의 인프런 Nodebird 리액트로 만들기 강의를 따라하는

프로젝트이고, 클론 코딩을 하며 배운 새로운 것들을 자유롭게 md파일로 작성하고자 한다.

### 아하! - 1
패스워드 일치와 관련된 코드를 하다가 제로초님의 코드를 보고 깨달은 것 1
```js
// 내 코드
const onChangePasswordCheck = (e) => {
    setPasswordCheck(e.target.value);
    if (password !== e.target.value) setPasswordError(true);
    else setPasswordError(false);
  }
// ZeroCho님 코드
const onChangePasswordCheck = (e) => {
    setPasswordCheck(e.target.value);
    setPasswordError(password !== e.target.value);
  }
```
비교연산자에서 값이 평가되는 boolean값을 바로 넣어줘도 되는 경우가 꽤 많을 것이다

그때에 나처럼 길게 하는 것이 아닌 간단하게 바로 넣어주는 코드로 짤 수 있다!

### useCallback
Hook의 특성상 리렌더링 시에 함수가 모두 재실행되는데 자식 컴포넌트로 넘겨주는 함수 역시

재할당이 되게 된다 그때 그것을 방지하기 위해서 함수마다 useCallback으로 감싸주면

deps 배열로 넘겨준 state의 변화 시에만 재실행하게 해줄 수 있다

기억하자! 자식 컴포넌트에 넘겨줄 때는 useCallback으로 감싸주자!

### dummy
프론트엔드 개발이 백엔드 api개발보다 우선될 때에 임시로 dummy라는 임시 객체 데이터를

이용하는 편이 좋다 잘 예상하고, 컴포넌트의 의존성을 잘 끊어서 사용하면 api가 개발되어도

동일한 로직으로 사용이 가능할 것이다!