# 180921 TIL (CSS - display, position)

Poiema web을 참고하여 작성하였음.

## 1. display 프로퍼티

#### display 프로퍼티는 총 4개로 구성된다

- block
- inline
- inline-block
- none

모든 HTML 요소는 아무런 CSS를 적용하지 않아도 기본적으로 브라우저에서 표현되는 디폴트값을 갖는다 inline이던 block이던 갖게 되는 것이다

**그리고 display는 상속되지 않는다!**

### 1.1 block 레벨 요소

- 항상 새로운 라인에서 시작한다
- 화면 크기 전체의 가로폭을 차지한다 (width 100%)
- width, height, margin, padding 프로퍼티의 지정이 가능하다
- block레벨 요소 내에 inline 레벨 요소를 포함할 수 있다
- block 레벨 요소들
  - div
  - h1-h6
  - p
  - ol
  - ul
  - li
  - hr
  - table
  - form

### 1.2 inline 레벨 요소

- 새로운 라인에서 시작하지 않으며 문장의 중간에 들어갈 수 있다, 즉 줄을 바꾸지 않고 다른 요소와 한 행에 위치한다
- content의 너비만큼 가로폭을 차지한다
- width, height, margin-top, margin-bottom 프로퍼티를 지정할 수 없다
- inline 레벨 요소 뒤에 공백(엔터, 스페이스)가 있는 경우, 정의하지 않은 space(4px)가 자동 지정된다
- inline레벨 요소 내에 block 레벨 요소를 포함할 수 없다
- inline 레벨 요소들
  - span
  - a
  - strong
  - img
  - br
  - input
  - select
  - textarea
  - button

### 1.3 inline-block 레벨 요소

- block과 inline 요소의 특징을 모두 갖는다 한줄에 표현되며 width, height, margin이 설정 가능하다
- content의 너비만큼 가로폭을 차지한다



## 2. position

