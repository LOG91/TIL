# Arrow Function (화살표 함수)
function 표현식에 비해 간략하게 함수를 표현하는 표현방식  
크게 두 가지 특성이 있다고 볼 수 있다  
- Short function (짧은 함수)
- No this binding (this binding이 없다)  

## Short function 
```js
let arr = [1,2,3,4,5];
arr.map(function(v){
  return v*2;
});
// function표현식을 =>를 이용하여 표현한다
arr.map((v)=>{
  return v*2;
});
// 매개변수가 하나라면 ()괄호를 생략할 수 있다
arr.map(v=>{
  return v*2;
})
// return문만 표현하려면 {}괄호와 return문을 함께 생략 가능하다
arr.map(v=>v*2);
```


## No this binding
```js
const myObj = {
	runTimeout() {
		setTimeout(function(){
            console.log(this === window);
        },200);
    }
}
// true를 리턴한다
// function() 익명 함수를 이용하면 this가 전역을 가리켜 true를 리턴한다
const myObj = {
	runTimeout() {
		setTimeout(()=>{
            console.log(this === window);
        },200);
    }
}
// false
// arrow function으로 바꿔주면 this는 runTimeout을 가리켜 false를 리턴한다
```
화살표 함수는 전역 컨텍스트에서 실행될 때 this를 새로 정의하지 않는다  
대신 코드에서 바로 바깥의 함수(혹은 class)의 this값이 사용된다  
이것은 this를 클로저 값으로 처리하는 것과 같다  
따라서 다음 코드에서 setInterval에 전달 된 함수의 this는  
setInterval을 포함한 function의 this와 동일한 값을 갖는다  
__from MDN__