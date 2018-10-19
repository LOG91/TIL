# 181019 TIL (CSS Transition)

트랜지션은 CSS 프로퍼티의 값이 변할 때 변화가 한 번에 나타나게 하는 것이 아니라

일정 시간에 걸쳐서 단계적으로, 애니메이션처럼 나타나게 하는 것이다

예를 들어 width값이 변화된다면 한 번에 변화된 값이 랜더링되는 것이 아니라

길이가 자연스럽게 늘어난다 (내부 동작은 상당히 복잡할 것이라 예상된다 ^^)

예제 코드를 보자

```css
div{
    width: 100px;
    height: 100px;
    background-color: red;
    transition: all 2s;
}

div:hover {
    width: 200px;
    backgrond-color: blue;
}
```

위와 같은 코드가 있다면 정사각형의 div box는 hover가 된다면 2초간

레드는 블루로, 길이는 100px에서 200px로 쭈욱 늘어날 것이다

참고로 all 2s는 변화하는 모든 동작에 대하여 2초간에 걸쳐하게 하는 것이다

#### 주의사항

아래와 같이 hover에 transition속성을 주게 되면 hover-on일 때만 작동한다

hover를 풀고 나갈 때는 2초에 걸치는 것이 아니라 바로 원 상태로 돌아온다!

```css
div:hover {
    width: 200px;
    backgrond-color: blue;
    transition: all 2s;
}
```

### 프로퍼티

- transition-property: 대상이 되는 CSS 프로퍼티를 지정
- transition-duration: 트랜지션이 일어나는 시간을 지정
- transition-timing-function: 트랜지션 효과를 위한 수치 함수 지정
- transition-delay: 프로퍼티가 변화한 시점과 트랜지션이 실제로 시작하는 대기 시간을 지정한다
- transition: 모든 트랜지션 프로퍼티를 한 번에 지정한다 (shorthand)

#### 주의사항2

모든 CSS 프로퍼티가 트랜지션의 대상이 될 수 없다

대상이 되는 프로퍼티는 다음과 같다

```
// Box model
width height max-width max-height min-width min-height
padding margin
border-color border-width border-spacing
// Background
background-color background-position
// 좌표
top left right bottom
// 텍스트
color font-size font-weight letter-spacing line-height
text-indent text-shadow vertical-align word-spacing
// 기타
opacity outline-color outline-offset outline-width
visibility z-index
```

**display는 트랜지션의 대상이 되지 않는다 이것을 모르고 none => block 때문에 한참 고생했다...!**

그리고 요소의 프로퍼티  값이 변화하면 브라우저는 프로퍼티 값의 변화에 영향을 받는

모든 요소의 기하값(위치, 크기)를 계산하여 layout작업을 수행한다

이것은 브라우저에게 스트레스를 주어 성능 저하의 요인이 된다

따라서 layout에 영향을 주는 트랜지션 효과는 회피해야 한다

layout에 영향을 주는 프로퍼티는 다음과 같다

```
width height padding margin border
display position float overflow
top left right bottom
font-size font-family font-weight
text-align vertical-align line-height
clear white-space
```

### transition timing function

- ease: 기본값이다 느리게 시작하여 점점 빨라졌다가 느려지며 종료
- linear: 시작부터 끝까지 등속 운동
- ease-in: 느리게 시작한 후 일정 속도에 다다르면 그 상태로 등속운동
- ease-out: 일정한 속도의 등속으로 시작해서 느려지며 종료
- ease-in-out: ease와 비슷하게 느리게 시작해 느려지며 종료

### transition shorthand

모든 트랜지션 프로퍼티를 한 번에 지정한다

```css
transition: property duration function delay
```

```css

div:nth-of-type(1) {
      /* property duration function delay */
      transition: width 1s ease-in 1s;
    }
    div:nth-of-type(2) {
      /* duration */
      transition: 1s
    }
    div:nth-of-type(3) {
      /* property duration */
      transition: width 1s
```

transition-duration은 반드시 지정해야 한다. 지정하지 않는 경우 기본값 0이 셋팅되어 어떠한 트랜지션도 실행되지 않는다

### Source: Poiemaseb