# 180810 TIL (Offline, DomContentLoaded, Event Delegation)

### 코드스쿼드 Offline review(180809)

- 코드스쿼드 LV3의 목표는 css가 어떤 것인지 이해해야 하는 것이다
- 웹사이트를 본다면 어떻게 짜졌는지 궁금해야 하고 내가 어떻게 하면 될지 대략적으로 알아야 한다
- css의 배치에 신경 써야 한다
- functional한 프로그래밍의 기본은 함수를 잘게 쪼개는 것이다, 고차함수를 써야 한다
- Class도 간결해야 한다! 본연의 역할만을!



### DOMContentLoaded

최초 HTML 문서가 완전히 로드 및 파싱되었을 때 발생한다

스타일시트나 이미지 및 서브프레임 로드가 끝나기를 기다리지는 않는다

그렇기에 모든 것이 끝나고 호출되는 load와는 다르다

모든 것이 load되기 전에 빠르게 처리해주어야할 작업들을 넣어놓을 수 있다

```js
document.addEventListener('DOMContentLoaded',function(){})
```

위와 같이 이벤트를 등록할 수 있다

위의 이벤트는 DOM Tree가 완성되었을 때 호출되는 함수다 그렇기에 내가 list마다 이벤트를 등록하는 함수를 실행하고자 했는데 아직 DOM 랜더링이 되지 않아서 이벤트 등록을 못하는 일을 이 함수를 통해서 막을 수 있다!



### Event Delegation

list의 item마다 이벤트를 등록해주고 싶을 경우가 있을 것이다

예제를 통해서 설명하겠다

```js
<ul>
  <li>
    <img src="https://images-na.,,,,,/513hgbYgL._AC_SY400_.jpg" class="product-image" >    </li>
  <li>
    <img src="https://images-n,,,,,/41HoczB2L._AC_SY400_.jpg" class="product-image" >    </li>
  <li>
    <img src="https://images-na.,,,,51AEisFiL._AC_SY400_.jpg" class="product-image" >  </li>
 <li>
    <img src="https://images-na,,,,/51JVpV3ZL._AC_SY400_.jpg" class="product-image" >
 </li>
</ul>
```

```js
var log = document.querySelector(".log");
var lists = document.querySelectorAll("ul > li");

for(var i=0,len=lists.length; i < len; i++) {
  lists[i].addEventListener("click", function(evt) {
     log.innerHTML = "clicked" + evt.currentTarget.firstChild.src;
  });
}
```

위와 같이 반복문을 돌면서 클릭 이벤트를 등록해줄 수 있을 것이다

이렇게 이벤트를 등록해주는 것이 지금은 4개이지만 리스트가 몇십, 몇백개가 된다면 브라우저는 그 많은 이벤트리스너를 다 기억하고 있어야 하는 문제가 발생한다

이 때 필요한 것이 이벤트 위임 (Event Delegation)이다

li마다 이벤트를 등록하던 것을 ul에 한 개만 등록을 하고 클릭이 발생했을 때 target값을 확인하여

그에 맞는 처리를 해준다고 보면 된다

```js
const itemNumberList = document.querySelectorAll('.coin_button_item');
    itemNumberList.forEach(v => {
      v.addEventListener('click', ({ target }) => {
        this.clickItemNumberButton(target);
      })
```

```js
const itemNumberList = document.querySelector('.coin_button_list_container');
    itemNumberList.addEventListener('click', ({ target }) => {
      if (target.className === 'coin_button') this.clickItemNumberButton(target);
    })
```

위의 첫번째처럼 반복문을 돌면서 이벤트를 등록하던 것을 두번째처럼 상위 태그의 한 번의 등록으로 변화시킬 수 있다

문제가 하나 발생할 수 있는데 위로 본다면 coin_button 클래스의 padding공간과 같이 target이 coin_button이 아닌 공간을 클릭하게 될 때가 문제가 된다

그 때를 대비하여 조건문을 달아서 클릭한 곳이 내가 원하는 곳일 때의 처리를 입력할 수 있다



### Prototype

이번에 프로토타입을 공부하면서 내가 쓰던 클래스가 어떻게 되어 있고 클래스가 왜 프로토타입으로 이루어져 있는지를 조금이나마 알 수 있게 되었다

우선 자바스크립트에서 객체는 쉽게 리터럴로 만들 수 있다

```js
var whale = {
  name : "log91",
  age : 28
  showName : function() {
    console.log(this.name);
  }
}

whale.showName(); //28
```

객체 안에서 this는 자기 자신을 가리킨다

```js
function Whale(name, age){
    this.name = name;
    this.age = age;
    this.showName = function(){
        console.log(this.name);
    }
}
```

위의 함수를 new를 통하여 선언하면 객체로 만들어줄 수 있다

이렇게 만들게 되면 동적으로 변경되는 값을 담을 수 있는 객체를 만들게 되는 것이다

```js
const w1 = new Whale('log91', 28);
w1 // {name:1og91, age: 28, showName: fn}
```

이렇게 객체로 만들어지는 것이고 이것을 통하여 사용된 함수를 생성자(constructor)라고 한다

이렇게 인스턴스를 만들어주는 것은 가능하지만 문제가 발생한다 중복인 것이다

showName과 같은 함수는 어느 인스턴스에서나 똑같은 일을 한다 코드가 같은 것이다

하지만 저렇게 생성 때마다 새로 만들어 줆으로 메모리가 낭비되는 것이다

그 때 필요한 것이 **Prototype**이다 사용은 아래와 같다

```js
function Whale(name, age){
    this.name = name;
    this.age = age;
}
var whaleObj = {
     showName: function(){
       console.log(this.name);
    }
}
Whale.prototype = whaleObj;
```

위와 같이 prototype을 이용하여 만들어주게 되면 놀라운 일이 생긴다

```js
const o1 = new Whale('log91', 28);
const o1 = new Whale('osk', 8);
o1 // {name: log91, age: 28}
o2 // {name: osk, age: 8}
// o1과 o2를 생성하는데 showName()은 보이지 않는다 하지만 부를 수 있다
o1.showName(); // log91
o2.showName(); // osk
```

바로 프로토타입을 이용하여 메모리를 공유하고 있기 때문이다

그렇기에 o1.showName === o2.showName 함수 자체는 true가 반환된다



#### Prototype 결론

지금껏 사용하던 클래스 안의 constructor와 그 밖에 선언되던 함수들이 어떻게 이용되고 있는 지를 이제서야 알게 됐다