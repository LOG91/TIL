# 181109 TIL (CSS 상속, 캐스캐이딩)

## 1. 상속(Inheritance)

상속이란 상위(부모, 조상)요소에 적용된 프로퍼티를 하위(자식, 자손)요소가 물려받는 것을

말한다, 상속 기능이 없다면 매번 프로퍼티를 각각 지정해줘야 한다

모든 프로퍼티가 상속이 되지 않고 되는 것, 안되는 것이 나뉜다!

대표적으로 color는 상속됨을 느껴왔었고 역시 됐었다

padding, margin, width, height와 같은 것은 역시 되지 않는다

#### 상속이 되지 않는 경우(상속받지 않는 요소 또는 상속되지 않는 프로퍼티)

inheritance키워드를 사용하여 명시적으로 상속받게 할 수 있다

```css
.text-red{
    color: red;
    width:100px;
    heigth:100px;
}
.text-red button{
    color: inherit;
}
```

```html
<div class="text-red">
    <button>whale</button>
</div>
```

button 요소는 상속을 받을 수 없다 하지만 위와 같이 inherit를 선언해준다면 가능하다!

또 width와 height는 상속이 안되는 프로퍼티지만 inherit를 이용하여 상속받을 수 있다!

## 2. 캐스캐이딩 (Cascading)

요소는 하나 이상의 CSS 선언에 영향을 받을 수 있다

이 때 충돌을 피하기 위해 CSS적용 우선순위가 필요한데 이를 **캐스캐이딩**이라고 한다!

캐스캐이딩의 세 가지 규칙

- 중요도: CSS가 어디에 선언되었는지에 따라 우선순위 높아짐
- 명시도: 대상을 명확하게 특정할수록 명시도가 높아지고 우선순위 높아짐
- 선언순서: 나중에 선언된 스타일이 우선 적용됨

### 2.1 중요도

CSS가 어디 선언되었는지에 따라서 우선순위가 달라진다

1. head 요소 내의 style 요소
2. head 요소 내의 style 요소 내의 `@import` 문
3. `<link>` 로 연결된 CSS 파일
4. `<link>` 로 연결된 CSS 파일 내의 `@import` 문
5. 브라우저 디폴트 스타일시트

### 2.2 명시도

1. !important

2. inline 스타일

3. 아이디 selector

4. 클래스 / 가상 선택자

5. 태그 선택자

6. 상속된 스타일

출처: 

http://victorydntmd.tistory.com/190

!important는 우선순위가 높지만 남발하는 것은 좋지 않다 (아직 공감 못함..)

### 2.3 선언 순서

```html
<html>
<head>
  <style>
    p { color: blue; }
    p { color: red; }

    .red { color: red; }
    .blue { color: blue; }
  </style>
</head>
<body>
  <p>Will be RED.</p>
  <p class="blue red">Will be BLUE.</p>
</body>
</html>

```

첫번째는 레드, 두번째는 블루가 된다

두번째 p태그에서 class="blue red"로 red가 뒤에 있어도 style태그에서 blue가 뒤에

선언되었기에 blue가 적용된다 (조금 헷갈렸다)

### Comment

inherit를 이용하여 width와 height지정에 나도 모르게 위에꺼 받는거 이런 정도로만 알고

사용했었는데 상속이 불가능한 요소에 상속을 명시적으로 해주고, 상속이 안되는 상위 요소의

프로퍼티를 상속을 명시적으로 해줄 수 있다는 사실을 깨달았다~~!