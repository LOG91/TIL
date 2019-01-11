# 190110 TIL (JS Object)

### 객체 생성방법

#### 1. 객체 리터럴을 사용

타 언어에 비해 매우 간단하게 중괄호`{}`만을 이용해 생성할 수 있다

#### 2. Object 생성자 함수

```js
const person = new Object();
person.name = "whale";
person.age = 29;
person.sayHello = () => console.log(`안녕 내 이름은 ${this.name}이야!`);
```

위와 같이 Object 생성자 함수를 이용한 방법이다
느끼는 바와 같이 굳이 사용될 이유가 없다 첫번째 말한 객체 리터럴이
더 간단하고 객체 리터럴 방식을 쓰면 된다
JS엔진은 객체리터럴을 만나면 내부적으로 Object생성자함수를 실행한다 (따라서 이것을 사용할 이유가 없다)

#### 3. 생성자함수 사용

위와 같은 방식으로 객체를 만들 때 비슷한 객체들을 계속해서 만들어간다면 아래와 같이 문제가 생길 것이다

```js
const person1 = {
  name: "osk",
  age: 29,
  sayHello: () => console.log("hello")
};

const person2 = {
  name: "osk",
  age: 29,
  sayHello: () => console.log("hello")
};
```

하지만 생성자함수를 사용한다면 마치 찍어내는 템플릿이 있는 것처럼
객체를 생성할 수 있다
방법은 간단하다 함수 앞에 new를 붙이고 생성하는 것이다

```js
const Person(name, age){
  this.name= name;
  this.age= age;
  this.sayHello= ()=>console.log('hello')
}
const p1 = new Person('osk',29);
```

위와 같이 간단하게 같은 객체를 계속 생성할 뿐만 아니라 this를 이용해 자기가 원하는 속성을 부여할 수 있다

- 생성자 함수 이름은 일반적으로 대문자로 시작한다. 이것은 생성자 함수임을 인식하도록 도움을 준다.
- 프로퍼티 또는 메소드명 앞에 기술한 this는 생성자 함수가 생성할 인스턴스(instance)를 가리킨다.
- this에 연결(바인딩)되어 있는 프로퍼티와 메소드는 public(외부에서 참조 가능)하다.
- 생성자 함수 내에서 선언된 일반 변수는 private(외부에서 참조 불가능)하다. 즉, 생성자 함수 내부에서는 자유롭게 접근이 가능하나 외부에서 접근할 수 없다.

### 프로퍼티 읽기, 수정, 생성

#### 읽기

점`.`표기법과 대괄호`[]`표기법을 이용하여 읽을 수 있다
프로퍼티 키가 유효한 자바스크립트 이름이라면 둘 다 이용이 가능하지만 유효하지 않다면 대괄호 표기법을 이용해야 한다

```js
const person ={
  name:'osk',
  'first-name':'seokki',
  1: 10,
}

person.1 // error;
person.['1'] // 10
person.[1] // 10 : person[1] -> person['1']
person.name // osk
person.first-name // error
person['first-name'] // seokki
```

#### 수정

소유하고 있는 프로퍼티에 새 값을 할당하면 value가 갱신된다

```js
person.name = "whale";
person.name; // whale
```

#### 삭제

delete 를 이용하여 프로퍼티를 삭제할 수 있다

```js
delete person.name;
person.name; // undefined
```

### for-in 문

for-in문은 객체를 순회하기 위한 반복문이다

```js
const person = {
  name: "osk",
  "first-name": "seokki",
  1: 10
};

for (let key in person) {
  console.log(key + person[key]);
}
```

위와 같이 사용을 하고 배열에는 사용하지 않는다 이유는 아래와 같다

- 객체의 경우, 프로퍼티의 순서가 보장되지 않는다. 그 이유는 원래 객체의 프로퍼티에는 순서가 없기 때문이다. 배열은 순서를 보장하는 데이터 구조이지만 객체와 마찬가지로 순서를 보장하지 않는다.
- 배열 요소들만을 순회하지 않는다.
  이와 같은 문제들로 ES6에는 배열을 위한 for-of문이 추가되었다

### Pass-by-reference

object type을 객체 타입 또는 참조 타입이라 한다. 참조 타입이란 객체의 모든 연산이 실제값이 아닌 참조값으로 처리됨을 의미한다. 원시 타입은 값이 한번 정해지면 변경할 수 없지만(immutable), 객체는 프로퍼티를 변경, 추가, 삭제가 가능하므로 변경 가능(mutable)한 값이라 할 수 있다.

따라서 객체 타입은 동적으로 변화할 수 있으므로 어느 정도의 메모리 공간을 확보해야 하는지 예측할 수 없기 때문에 런타임에 메모리 공간을 확보하고 메모리의 힙 영역(Heap Segment)에 저장된다.

이에 반해 원시 타입은 값(value)으로 전달된다. 즉, 복사되어 전달된다. 이를 pass-by-value라 한다.

```js
var foo = {
  val: 10
};

var bar = foo;
console.log(foo.val, bar.val); // 10 10
console.log(foo === bar); // true

bar.val = 20;
console.log(foo.val, bar.val); // 20 20
console.log(foo === bar); // true
```

foo 객체를 객체 리터럴 방식으로 생성하였다. 이때 변수 foo는 객체 자체를 저장하고 있는 것이 아니라 생성된 객체의 참조값(address)를 저장하고 있다.

변수 bar에 변수 foo의 값을 할당하였다. 변수 foo의 값은 생성된 객체를 가리키는 참조값이므로 변수 bar에도 같은 참조값이 저장된다. 즉, 변수 foo, bar 모두 동일한 객체를 참조하고 있다. 따라서 참조하고 있는 객체의 val 값이 변경되면 변수 foo, bar 모두 동일한 객체를 참조하고 있으므로 두 변수 모두 변경된 객체의 프로퍼티 값을 참조하게 된다. 객체는 참조(Reference) 방식으로 전달된다. 결코 복사되지 않는다.

### Pass-by-value

원시 타입은 값(value)으로 전달된다. 즉, 값이 복사되어 전달된다. 이를 pass-by-value(값에 의한 전달)라 한다. 원시 타입은 값이 한번 정해지면 변경할 수 없다.(immutable) 또한 이들 값은 런타임(변수 할당 시점)에 메모리의 스택 영역(Stack Segment)에 고정된 메모리 영역을 점유하고 저장된다.

immutable에 대한 상세한 내용은 객체와 변경불가성(Immutability)을 참조하기 바란다.

```js
// Pass-by-value
var a = 1;
var b = a;

console.log(a, b); // 1  1
console.log(a === b); // true

a = 10;
console.log(a, b); // 1  10
console.log(a === b); // false
```

변수 a는 원시 타입인 숫자 타입 1을 저장하고 있다. 원시 타입의 경우 값이 복사되어 변수에 저장된다. 즉, 참조 타입으로 저장되는 것이 아니라 값 자체가 저장되게 된다. 변수 b에 변수 a를 할당할 경우, 변수 a의 값 1은 복사되어 변수 b에 저장된다.

### Reference

- Poiema Web
