# Execution Context (실행 컨텍스트)

### Execution context?

Execution : 실행 Context : 문맥  
쉽게 표현하면 실행 환경이라고 할 수 있다
실행 컨텍스트는 자바스크립트를 이해하는데 필수적이다
scope, hoisting, this, function, closure 등의 동작 원리를 담고 있는 자바스크립트의
핵심원리라고 볼 수 있다
과정을 살펴보면 코드를 실행할 때에 모든 것을 포함하는 전역 컨텍스트가 먼저 생성된다
이곳은 모든 것을 관리하는 환경이고 페이지가 종료될 때까지 유지된다
그리고 여기에서 함수를 호출할 때에 컨텍스트가 하나씩 더 생긴다

실행 컨텍스트의 특성

- 전역 컨텍스트 생성 후, 함수를 호출할 때마다 컨텍스트가 생성된다
- 컨텍스트는 VariableObject(arguments, variable), scope chain, this로 구성된다
- 컨텍스트 생성 후 함수가 실행된다 변수들은 변수 객체 안에서 값을 찾고 없다면 스코프체인을 따라 올라가면서 찾는다
- 함수 실행이 마무리되면 해당 컨텍스트는 사라진다 (클로저 제외),  페이지가 사라지면 전 역 컨텍스트가 사라진다
- this는 따로 설정하지 않는다면 window를 가리킨다 바꾸는 방법은 new를 호출하거나 다른 함수에 bind를 시키는 것이다



### 실행 과정

실행 컨텍스트가 생성된 후 아래의 과정이 실행된다

1. 스코프 체인의 생성과 초기화
2. Variable Instantiation(변수 객체화) 실행
3. this value 결정

__1.스코프 체인의 생성과 초기화__

실행 컨텍스트가 생성된 이후 가장 먼저 스코프 체인의 생성과 초기화가 실행된다. 이때 스코프 체인은 전역 객체의 레퍼런스를 포함하는 리스트가 된다.

__2. 변수 객체화 실행__

1. (Function Code인 경우) **매개변수(parameter)**가 Variable Object의 프로퍼티로, 인수(argument)가 값으로 설정된다.
2. 대상 코드 내의 **함수** 선언(함수 표현식 제외)을 대상으로 함수명이 Variable Object의 프로퍼티로, 생성된 함수 객체가 값으로 설정된다.(**함수 호이스팅**)
3. 대상 코드 내의 **변수** 선언을 대상으로 변수명이 Variable Object의 프로퍼티로, undefined가 값으로 설정된다.(**변수 호이스팅**)

__3. this 결정__

변수 선언 처리가 끝나면 다음은 this value가 결정된다. **this value가 결정되기 이전에 this는 전역 객체를 가리키고 있다가 함수 호출 패턴에 의해 this에 할당되는 값이 결정된다.**전역 코드의 경우, this는 전역 객체를 가리킨다.

**반드시 위의 순서대로 실행된다고 한다**

```js
var name = 'log91'
function sayHello(name){
    console.log('Hello ' + name);
}
sayHello(name);
```

전역 컨텍스트를 객체 형식으로 표현해보자면 아래와 같다

```js
'전역 컨텍스트' : {
    변수객체 : {
        arguments : null,
        variable : ['name', 'sayHello', 'callMe']
    },
    scopeChain : ['전역 변수객체'],
    this : window
}
```

그 다음 코드를 읽으며 변수에 대입된다 (함수는 선언식이라 지금 대입된다)

```js
variable : [{name : 'log91'}, {sayHello : Function},{hello : Function}]
```

sayHello 컨텍스트를 객체 형식으로 표현하면 아래와 같다

```js
'sayHello 컨텍스트' : {
    변수객체 : {
        arguments : [{name : log91}]
        variable : null,
        scopeChain : ['sayHello 변수객체', '전역변수 객체'],
        this : Window
    }
}
```

### Comment

- 컨텍스트라는 곳에 매개변수, 변수, 스코프, this정보가 추가되고 그곳을 참조하여 실행한다는 사실을 새롭게 알았고 이것을 정확히 이해한다면 자바스크립트 코딩에 아주 많은 도움이 될 것 같다