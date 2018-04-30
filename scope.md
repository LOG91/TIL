# scope

> scope : 범위

scope는 범위다

자바스크립트에서는 lexical scope라고 어휘적 범위라고 하는데 함수를 호출할 때가  

아닌 함수를 선언할 때 scope가 정해진다  

scope에 대해 더 알아보기 전에 전역 변수와 지역변수에 대하여 알아보자  

### 지역(local)변수, 전역(global)변수

지역변수는 함수 안에서 선언한 변수, 전역변수는 함수 밖, 즉 아무 함수 안도 아닌 가장 밖에 선언된 함수다

```js
var a = 'whale';
var b = 'killerWhale';
function callMe() {
    var a = 'log91';
    var c = 'loglog';
    console.log(a);
    console.log(b);
}
callMe();
// 'log91'
// 'whale'
console.log(c); // ReferenceErro : c is not defined

```

위에서 console은 log91과 whale을 찍는다  

console.log(a)에서 지역변수 a를 호출하기 때문에 log91이 찍히고  

console.log(b)에서는 지역변수가 없기 때문에 전역변수의 b를 호출한다  

위에서 알 수 있듯이 지역변수에 호출하는 값이 없으면 전역변수를 참조해 호출한다  

하지만 console.log(c)의 경우처럼 전역에서는 지역변수의 변수를 참조할 방법이 없다  

여기서 알아야 할 것이 바로 __scope__다!  

### Scope

위에 말한 것처럼 함수는 선언될 때에 자신의 scope환경(?)이 조성된다  

함수는 선언되는 객체가 생성된다 그곳의 프로퍼티에 [[scope]]를 생성하고 그곳이 scope가 되는 것이다  

그 때 [[scope]]에 함수객체가 참조할 수 있는 scope들이 객체로 들어가 있다  

그 [[scope]]의 집합을 Scope Chain이라고 한다  

변수의 검색은 이 scope chain을 통해서만 탐색된다  

위에서 callMe의 scope에서 내가 찾는 변수 b를 발견하지 못하여 scope chaining을 이용해 상위의 global scope에서 b = 'whale'을 찾아낸다  

scope chaining은 가까운 scope를 우선으로 찾아낸다

```js
var cc = 'rok';
function a(){
    var aa = 'whale';
    var bb = 'log91'
    function b(){
        var aa = 'killerWhale';
        function c(){
            console.log(aa);
            console.lob(bb);
            console.log(cc);
        }
        c();
    }
    b();
}
a();
```

위에서 console.log(aa)가 c scope내에서는 없기에 그 상위 scope b에서 찾아내서 killerwhale을 호출하는 것이다. 

console.log(bb)에서 bb는 b에도 없기에 a scope까지 가서 찾고 cc는 a scope에도 없어서 global scope까지 가서 rok변수를 찾아낸 것이다. 

c의 scope chaining은  c, b, a, global을 가진다고 볼 수 있는 것이다!  

### Lexical scope

해석하면 어휘적 범위이고 정적 스코프라고도 한다  

스코프는 함수를 호출할 때가 아닌 선언할 때 생긴다는 것을 말한다  

```js
var name = 'whale';
funciton log() {
	console.log(name);
}
function wrapper() {
    name = 'log91'
    log();
}
wrapper();
```

답은 log91입니다. log호출 전에 name이 log91로 변경됐기 때문이죠

```js
var name = 'whale';
funciton log() {
	console.log(name);
}
function wrapper() {
    var name = 'log91'
    log();
}
wrapper();
```

하지만 위는 whale을 호출합니다  

스코프는 함수를 __선언__할 때 생기기 때문에 log는 wrapper scope와는 관련이 없습니다  

그렇기에 가장 가까운 global함수의 whale을 불러오는 것이지요.  



### Comment

자바스크립트에 대하여 공부할수록 그냥 느낌으로 그럴 것 같던 것들에 대하여 알게 되는 것 같다  이것을 내가 설명할 수 있을 때까지 주기적으로 복습하는 것이 필요한 것 같다  

scope개념에 대하여 전보다는 확실히 알게 된 것 같다!

