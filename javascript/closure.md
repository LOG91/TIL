# Closure

## Closure란?
A함수 안에 B함수가 있을 때에 A의 scope에 선언된 지역변수를 B함수의 입장에서는  
 Closure라고 한다  
그래서 closure scope라는 명칭을 쓰는 것도 어색하지 않다

예를 들어 A함수 안에 또 다른 B함수를 만들고 리턴값을 B함수 자체로 리턴해주면 외부에서 B함수를 호출하는데 A함수 스코프에 사용된 다른 변수들에 접근하여 사용하는 효과를 내주는 자바스크립트의 특수한 성질을 이용하는 것이다  
좀 더 명확한 설명을 위해서는 콜스택에 대한 이해가 필요하다  
> 콜스택 : 함수를 선언할 때에 함수는 콜스택이라는 메모리에 쌓인다 쌓일 때에 함수 안에 있는 모든 변수와 함수들이 저장되는 것이다 예를 들어
```js  
 function A(){
   var a,b = 1;
   function B(){
     return a;
   }
   return B;
}
let test = A();
test();
```
>위에서 A()를 실행한다면 변수 a, b와 함수 B()가 메모리에 할당된다  
그리고 return문을 만나서 B함수를 반환하고 A()함수의 모든 변수는 메모리에서 사라진다

클로저는 이 스택의 성질을 위배시킨다고 할 수 있는 방식이다

```js
function makeFunc() {
  var a = 'whale';
  var b = 'dolphin';

  function returnAB() {
    result = `${a}이랑 ${b}이 살아있지롱~`;
    return result;
  }
  return returnAB;
}

var callAB = makeFunc();
console.log(callAB());

```
var callAB =  makeFunc()에서 makeFunc()이 호출될 때에
makeFunc()함수가 실행되고 변수 a,b가 선언되고 함수 returnAB가
실행된다 그리고 returnAB함수의 리턴값이 아닌 returnAB 함수 자체를 반환한다  
결과적으로 callAB는 returnAB 함수를 참조하게 된다  

그리고 다음 라인에서 callAB()를 호출한다 그러면 returnAB()함수의 반환값인 result를 반환한다
여기서 중요한 것은 callAB를 호출할 때에 전에 makeFunc()의 호출이 끝나서 스택에서 비워져서 a,b값이 사라졌음에도 불구하고 makeFunc()를 호출할 떄 저장된 whale과 dolphin을 참조해서 a, b가 undefined가 아닌 whale과 dolphin을 반환한다는 점이다  
이것을 이용하여 외부에서 참조할 수 없게 변수들을 가둘 수도 있고  
전역변수를 없앨 수도 있다