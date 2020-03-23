# 출석부 Project - 회고 6

### Async Await
api를 수정한 일이 있었는데 그 후 계속 에러가 났다

중요한 것은 그 api가 사용되지도 않았는데도 계속 나는 것이었다

다행히 그리 오랜 시간이 걸리진 않았지만 코드에서 복붙을 하느라 await가 따라왔는데

api 함수엔 async 키워드가 붙어 있지 않았다

그래서 생긴 문제였는데 이것을 디버깅하는 것은 에러 메시지로 가능한 것이 아니었다

예전에도 두 번 정도 이런 문제를 겪었어서 이제 잊지 않기 위해 작성한다!

### Destructuring의 무분별한 사용의 폐해 + 게으름의 폐해
Home 컴포넌트가 8번이나 리렌더링되는 상황을 직면하고 엄청나게 스트레스를 받으면서

이 문제를 디버깅했다 state, match, dispatch, props를 다 지워가면서 해봤다

도저히 답이 안 나올 것 같던 그 순간 보인 것은 아래 코드였다

```js
  const {modalOpend, networkCells, sheets } = useSelector(state => state.checker);
```
지푸라기라도 잡는 심정으로 설마 저 state를 전체를 받아오기 때문은 아닐까 하고 아래와 같이 수정했다

그 결과 기적적으로 리렌더링이 두 번만 되었다

state를 전체로 받아오니 온갖 변화에 다 리렌더링이 일어났던 것이다

```js
  const modalOpend = useSelector(state => state.checker.modalOpend);
  const networkCells = useSelector(state => state.checker.networkCells);
  const sheets = useSelector(state => state.checker.sheets);
```