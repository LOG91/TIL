# 문서 객체 모델 (Document Object Model)
## DOM이란 무엇인가?
DOM은 HTML 문서의 모든 요소에 접근하는 방법을 정의한 API다.  
  
  DOM객체는 텍스트와 이미지, 하이퍼링크, 폼 엘리먼트 등 각 문서 엘리먼트를 나타낸다.  
  자바스크립트 코드에서는 HTML을 만들어내기 위해 DOM 객체에 접근해서 조작할 수 있다.

## 속성
### 태그.nodeType
일단 태그를 선택한 후 nodeType 속성을 검색하면 해당 태그의 종류를  
알려주는 숫자가 나옵니다  
- 1 : Element
- 3 : 텍스트
- 8 : 주석
- 9 : Document
- 10 : DOCTYPE
- 11 : Document Fragment
중간에 빈 2,4,5,6은 더 이상 쓰이지 않는 숫자이고 7도 거의 쓰지 않습니다
크게 텍스트 노드(3번)과 일반 노드(1번) 을 나누는데만 쓰인다
### 태그.children, 태그.childNodes
```html
<body>
<form id="info" name="userinfo" method="get" action="/info.html">
        <p>회원정보</p>
        <p>이름 : <input type="text" name="name"></p>
        <p>이메일 : <input type="text" name="email"></p>
        <p>성별 : <select name="gender">
        <option>비공개</option>
        <option>남자</option>
        <option>여자</option>
      </select></p>
        <p class="transfer"><input name="send" type="button" value="전송"></p>
</form>
</body>
```
자식으로 갈 때에는 children(텍스트 노드 제외), childNodes(텍스트 노드 포함)를 사용합니다  
```
document.body.children[0]
-> <form id="info" name="userinfo" method="get" action="/info.html"> 
document.body.children[0].children[0]
-> <p>회원정보</p>
```
이런 식이 되는 것입니다

### id, class
위에 보면 form 에 id속성, p에 class 속성이 있음을 볼 수 있다  
이것을 이용해도 해당 노드에 접근할 수 있다
```js
document.getElementsByClass('transfer');
document.getElementById('info');
```
### 스타일시트 (Stylesheet)
HTML 및 DOM과 긴밀하게 묶이는 주제가 스타일시트다  
각 요소에 하나하나 접근해서 글짜 크기와 색을 바꿔주는 것이 아니라  
스타일시트를 이용해서 편하게 그리고 동시에 바꿔줄 수 있다  
여기에서 CSS가 쓰이는 것이다

## style 프로퍼티  
각 DOM 노드에는 style 프로퍼티가 있으며, 이것을 이용해 해당 노드의  
스타일을 조작할 수 있다  
```js
// class이름이 in인 노드의 색을 red로 변경
document.getElementsByClassName('in')[0].style.color = 'red';
// id이름이 info인 노드를 사라지게 만듦
document.getElementById('info').style.display = 'none';
```
***
