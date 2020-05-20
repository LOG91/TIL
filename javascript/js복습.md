모든 선언문은 호이스팅 된다
var, let, const, function, function*, class

변수는 3단계에 걸쳐서 생성된다

1. 선언 단계
변수 객체(Variable Object)에 변수를 등록한다. 이 변수 객체는 스코프가 참조하는 대상이 된다.

2. 초기화 단계
변수 객체(Variable Object)에 등록된 변수를 메모리에 할당한다. 이 단계에서 변수는 undefined로 초기화된다.

3. 할당 단계
undefined로 초기화된 변수에 실제값을 할당한다.

var 키워드는 호이스팅될 때 1, 2번 과정이 동시에 일어난다
그래서 아래와 같은 상황에 에러 없이 undefined를 볼 수 있다
console.log(foo); // undefined
var foo = 123;
console.log(foo); // 123

하지만 let과 const는 hoisting할 때 1번 과정만 먼저 일어나기 때문에
위의 코드를 let, const로 교체할 시에 reference error를 얻게 된다

### 문과 표현식
자바스크립트 코드는 문으로 되어 있다
이 문은 엔진에게 요청을 하는 코드라고 할 수 있다
그리고 표현식은 문에 들어가 있는 식이라고 할 수 있는데 무언가 헷갈릴 수 있지만 다르다

표현식은 평가되어져 값을 만드는 행위를 한다
표현식으로 평가한 값을 통하여 문은 엔진에게 명령을 하게 되는 것이다

문에는 var, let, const, function, if, while, for 문이 있을 수 있다

### 할당 연산은 표현식이다
a = 100; 이 할당문은 이 자체로 표현식이어서 할당된 값으로 평가된다

때문에 console.log(a = 100); 은 100을 리턴한다