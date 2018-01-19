# 이벤트 (Event)
웹 페이지에서 실제로 유용한 기능을 추가하려면 문서를 조사하고 수정하는 것 이상의  
일을 할 필요가 있다. 즉, 사용자의 행동을 감지해서 거기에 응답할 수 있어야 한다.  
이 때에 이벤트가 필요하다.

## 이벤트 헨들러
키 누름, 스크롤, 마우스 클릭, 마우스 움직임까지도 모두 브라우저에 의해 이벤트로 바뀌며,  
그러한 이벤트를 처리하는 코드를 작성할 수 있다.  
기본적으로 브라우저 이벤트가 동작하는 방식은 아주 간단하다.  
특정 DOM 노드상의 특정 이벤트 타입에 핸들러를 등록하는 것이 가능하고 이벤트가 발생하면  
해당 이벤트에 등록 된 핸들러가 호출된다

## 핸들러 등록
- 이벤트 핸들러 등록
- 이벤트 객체 획득
- 이 객체에서 정보 추출
- 이벤트가 처리됐다는 신호 전달
  
  한 가지 아쉬운 점은 브라우저마다 이벤트 지원과 이름이 다르다는 것이다

```js
 // 이 함수를 이용하면 어느 모델이 지원되는지 확인한 후 좀 더 편리하게 등록이 가능하다
function registerEventHandler(node, event, handler) {
            if (typeof node.addEventListener == 'function')
                node.addEventListener(event, handler, false);
            else
                node.attachEvent("on" + event, handler);
        }

 // 첫번째 인자에 마우스를 올려놓을 때에 alert 호출
var ment = 'Hello event';
registerEventHandler(vi, "mouseover", function(event) {
        event = event || window.event;
        if ((event.target || event.srcElement) == vi)
            alert(ment);
            });
 // body요소를 클릭할 때애 클릭한 좌표 r1요소에 출력
var r1 = document.body.children[0];
registerEventHandler(document.body, "click", function(event) {
    event = event || window.event;
    r1.value = event.clientX + ", " + event.clientY;
});

```
위와 같이 함수를 등록하게 편리하게 사용할 수 도 있다
        