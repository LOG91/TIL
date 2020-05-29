# 200528 TIL - CSS transition
### 5월의 새해 다짐
금일부터 TIL을 꾸준히 실천하기로 했다

블로그를 시작하고 싶지만 취준이 급한 지금 욕심이라 생각되어 md로 진행한다

사실 글쓰는 것이 별로 중요하지 않다고 생각했고, 시간이 아깝다고 느꼈다

하지만 주변에 사람들이 개발자로 일하며 느끼는 중요한 것은 글 잘 쓰고,

정리 잘하는 것이 능력이라는 것이다

사람들에게 나의 상태와 의견을 나눌 수도 있고, 작성하며 생각도 정리되기 때문이다

물론 이외에도 장점이 많겠지만 이 두 가지 부분만 놓고서라도 중요하다고 생각한다

아무튼 그래서 꼭 1일 1깡이 아닌 1일 1TIL을 하기로 했다

### transition property
트랜지션은 css의 프로퍼티 중 하나다

트랜지션만 잘 써도 있어보이는 UI를 제공할 수 있다

트랜지션은 CSS 속성을 변경할 때 애니메이션 속도를 제어하는 방법을 제공한다

빨간색 배경의 div 태그를 파란색으로 바로 변경하는 것이 아니라 서서히 변화시킨다 (싱기)

위치를 변경할 때 그곳으로 변경 위치로 바로 렌더링이 아닌 그 위치로 서서히 이동을 시킨다

> 두 상태 사이의 전환을 포함하는 애니메이션은 시작 상태와 최종 상태 사이의 상태가
> 브라우저에 의해 암묵적으로 정의되기 때문에 종종 암묵적인 전환이라고 합니다. from MDN

### 속성
`transition: all 2s ease;` 이런 식으로 shorthand로 사용할 수 있다

하지만 동기화 매개변수 문제(?) 와 CSS debugging에 좋지 않아 추천하지 않는다고 한다

__항상 이렇게 지정해왔던 나다__

그럼 일일이 지정해주는 방법에 대하여 알아보자

#### transition-property

애니메이션을 적용할 속성만 입력해주면 된다 다중 입력이 가능하다

이곳에 기록되지 않는 속성인 경우 즉시 상태만 변화한다 (애니메이션 적용x)

```css
.cls {
  transition-property: width height background-color font-size left top transform;
}
```

#### transition-duration

애니메이션이 적용되는 기간을 지정해준다

```css
.cls {
  transition-duration: 0.5s;
}
.cls2 {
  transition-duration: 2s;
}
```
s는 초를 의미한다. 0.5초 안에 변화가 일어난다면 빠르게 변화해야하기 때문에

태그의 이동 같은 경우 빠르게 지나갈 것이며, 색깔이 변하는 애니메이션도 순식간에 변화할 것이다

#### transition-timing-function

트랜지션이 어떻게 적용될 것인지를 정의한다

ease, ease-in, linear, step-end, step-start 등이 있다

ease는 서서히 변화하다가 duration이 끝나갈 때 급속도로 빨리 변하는 것을 나타내고,

linear는 이름 그대로 일정한 속도로 처음부터 끝까지 변하게 된다

#### transition-delay

트랜지션이 몇 초 후에 실행될 것인지를 정의한다

#### transition shorthand
```css
.cls {
    transition: <property> <duration> <timing-function> <delay>;
}
```

### transition 사용시 주의사항
- adding the element to the DOM using .appendChild()
- removing an element's display: none; property.

다음과 같은 두 경우에는 마지막 상태값만 반영이 되어 애니메이션이 적용되지 않는다

display: none => display: display 를 자주 시도해본 적이 있는데 애초에 불가능하다

방법은 setTimeout을 이용한 방법이 있다

### Javascript를 활용한 흥미로운 예제 (MDN예제)
```js
var f = document.getElementById('foo');
document.addEventListener('click', function(ev){
    f.style.transform = 'translateY('+(ev.clientY-25)+'px)';
    f.style.transform += 'translateX('+(ev.clientX-25)+'px)';
},false);
```
```css
p {
  padding-left: 60px;
}

#foo {
  border-radius: 50px;
  width: 50px;
  height: 50px;
  background: #c00;
  position: absolute;
  top: 0;
  left: 0;
  transition: transform 1s;
}
```
You can play with this here: http://jsfiddle.net/9h261pzo/291/

위 코드를 이용하면 클릭한 곳으로 빨간색 공이 이동하는 나름대로 재미있는 애니메이션을 경험할 수 있다


## Reference
- MDN https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions