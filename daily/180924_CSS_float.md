# 180924 TIL (CSS float)

이 글은 PoiemaWeb을 참고하여 작성됐습니다

float프로퍼티는 주로 레이아웃을 구성할 때 블록 레벨 요소를 가로로 정렬하기 위해 사용되는 중요한 기법이다

flex를 이용하면 더욱 간단하게 구현이 가능하지만 지원하지 않는 IE를 고려한다면 float을 사용해야 한다..!

float프로퍼티는 해당 요소를 다음 요소 위에 떠 있게 한다

여기서 떠있다는 것은 기본 레이아웃 흐름에서 벗어나 요소의 모서리가 페이지의 왼쪽이나

오른쪽에 이동하는 것이다!

width 프로퍼티를 선언하지 않은 block레벨 요소에 float프로퍼티가 선언되면 width가 inline요소와 같이 content에 맞게 최소화되고 다음 요소 위에 떠있게 된다

```
//css
.box{
	font-size:30px;
	line-heigth:50px;
	height:50px;
    float:left;
}

.d1{
    float:left;
    background-color: red;
}
.d2{
    background-color: orange;
}

//html
<div class="box d1">D1</div>
<div class="box d2">D2</div>

```



두 개의 div가 나란히 있을 때에 앞 쪽에만 선언해줄 때에 d1에는 width가 inline요소와 같이 content에 맞게 최소화 되고 d2클래스 위에 부유하게 된다

주의할 것은 d1클래스가 d2위에 떠있다고 해서 d2클래스요소의 width가 줄어드는 것이 아니라 100%를 유지하는 것이다

d2에는 float를 선언하지 않았기 때문이다

이를 해결하는 가장 쉬운 방법은 float를 선언하지 않은 요소(d2)에 `overflow:hidden`프로퍼티를 선언하는 것이다

`overflow:hidden`프로퍼티는 자식 요소가 부모 요소의 영역보다 클 경우 넘치는 부분을 안보이게 해주는 역할을 하는데 여기서는 float프로퍼티가 없어서 제대로 표현되지 못하는 요소를 제대로 출력해준다!

두번째 요소에도 float 프로퍼티를 선언하면 `overflow: hidden` 프로퍼티는 선언하지 않아도 되지만 너비가 최소화된다.