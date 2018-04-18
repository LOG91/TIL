# Class
ES6에서 추가된 문법으로 기존의 prototype기반의 상속보다  
명료하게 상속을 다룬다  
class라는 대단한 패러다임이 추가된 것은 아니다는 것을 알아야 한다  

## 사용
선언식과 표현식 두 가지로 사용할 수 있다
### 1. 선언
```js
class Health {
    constructor(name, lastTime) {
        this.name = name;
        this.lastTime = lastTime;
    }

    showHealth() {
        console.log('안녕하세요' + this.name);
    }
}
```
> __Hoisting__  
> 함수 선언과 클래스 선언의 차이점이 하나 있다 호이스팅이다  
> 함수 선언은 호이스팅이 일어나지만 클래스 선언은 그렇지 않다
>```js
>const h = new Health('whale');
> class Health{...} // Reference Error
>```
### 2. 표현
```js
const Health = class {
    constructor(name, lastTime) {
        this.name = name;
        this.lastTime = lastTime;
    }

    showHealth() {
        console.log('안녕하세요' + this.name);
    }
}
```
## Constructor
생성자다 class body 내에 한 개만 선언할 수 있다  
두 개가 선언된다면 SyntaxError가 발생한다!  
이곳에 속성들을 담을 수 있고 초기화 내용을 처리할 수 있다  
super키워드를 사용해 부모 클래스의 constructor를 호출할 수 있다  
```js
class Health{
  constructor(name){
    this.name = name;
  }
}
```

## Prototype VS Class
class는 내부적으로 prototype으로 동작한다  
하지만 class는 prototype보다 높은 가독성을 자랑하기 때문에  
ES6이후부터는 class를 쓰는 것이 좋다는 사람이 많다  
아래의 두 코드는 같다
```js
// Prototype
function Health(name) {
    this.name = name;
}
Health.prototype.showHealth = function() {
    console.log(this.name + '님 안녕하세요');
}
const h0 = new Health('log91');
h0.showHealth(); // log91님 안녕하세요
// Class
class Health {
    constructor(name, lastTime) {
        this.name = name;
        this.lastTime = lastTime;
    }

    showHealth() {
        console.log('안녕하세요' + this.name);
    }
}
const h1 = new Health('whale');

// 알아보기 위해서 크롬 개발자 도구에서  
// console.log(h1);을 해본다면 Object를 아래와 같이 반환한다  
console.log(h1);
{name : whale, lastTime : undeifned} 그리고
__proto__에 constructor와 showHealth함수가 있는 것을 알 수 있다

// 또 한가지 prototype이 function인 것처럼
// toString.call(Health))를 찍어보면
// [object Function]이 나온다!!
```

## Character
- class 내부는 strict mode다
- extends를 이용하여 상속할 수 있다

## Comment
사실 JS의 prototype을 사용해보기 전에 class를 배워서 무언가  바로class로 진입하면 될 것 같다  
그래도 내부 구조를 알 수 있고 조금은 이해해서 좋았다