# 회고 - 출석부 Project 4
출석부에 관하여는 마지막으로 쓰는 회고가 될 것이다 아멘

### sortable.js
당연하게 등록된 데아터의 순서를 변경해주는 기능이 있어야 한다

그래서 드디어 처음으로 이 프로젝트에 라이브러리를 도입했다

라이브러리는 **sortable.js**!

드래그앤드롭 방식으로 순서를 정렬해주는 라이브러리다

#### 편리함
이 라이브러리는 상위 그러니 ul 과 li 관계라면

ul에 등록해주면 편리하게 사용할 수 있다

drag를 시작하는 시점, 끝나느 시점에 이벤트를 걸어줄 수 있고

동작시 애니메이션에 관한 상세한 동작도 파라미터로 등록할 수 있다

#### 삽질
안타깝게도 이 라이브러리를 사용하면서 엄청난 트러블슈팅을 해야 했다

onEnd 메서드 (드롭 시 이벤트)에 순서를 변경하는 리덕스 함수를 넣었고

문제 없이 동작하여 리덕스 스테이트는 바뀌었다

하지만 다음에 동작하는 이벤트에서는 여전히 전의 state를 참고하는 것이었다

이때부터 클로저, 스코프, 비동기 모든 나의 JS지식이 싸움을 시작했고,

답을 찾기가 쉽지 않았다

끝내 발견하게 된 것은 이벤트를 등록해준 것을 취소하지 않아서였다

sortable에는 destroy 메서드가 제공되는데 그것으로 취소를 하고 다시 등록을 해주면 된다

#### 깨달은 것
useEffect에 대하여 많이 경험하고 이벤트 등록을 취소해줘야 하는 시점에 대하여서도

깊이있게 깨닫는 시간이었다

useEffect가 라이프사이클을 다루는 데 복잡해보였는데 state별로 effect를 넣어준다는 식으로

접근을 하니 간편한 점이 많았고 이번 이슈도 willUnmount, 즉 useEffect의 리턴으로 해결했다