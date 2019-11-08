## 190918TIL (Inside JS 책)

### 데이터타입과 연산자

한 번 생성된 문자열은 읽기만 가능하고 수정은 불가능하다

```
var str = 'test';
str[0] = T;
console.log(str); // test
```

#### null과 undefined

undefined는 JS에서 변수에 값이 할당되지 않았을 때 할당되는 값이다

값이자 타입이다

```
typeof undefined // undefined
```

#### JS에서 객체 생성 방법

- 객체 리터럴을 이용한 방법

```
const obj = {a: 'whale', b: 91};
```

- Object객체를 이용한 방법

```
const obj = new Object();
```

- 생성자 함수 이용

```
const Con = function(){
...
}
const obj = new Con();
```

#### 객체의 프로퍼티 읽는 방법 두 가지

점(.) 표기법과 대괄호([]) 표기법이 있다

대괄호 표기법만 사용해야할 경우: 표현식, 숫자, 예약어

#### 객체 프로퍼티 삭제 방법

delete 연산자를 사용한다, 객체의 프로퍼티는 삭제가능하지만 객체 자체 삭제는 불가함

#### Call by Value, Call by Reference

기본 타입과 참조 타입을 함수의 인자로 넘겨줄 때 차이가 난다

기본 타입의 경우엔 값에 의한 호출(Call by Value)가 일어나서 넘겨주는 값이 복사되어 넘겨진다, 그래서 값을 수정해도 원래 변수는 변하지 않는다
하지만 참조타입의 경우 참조에 의한 호출(Call by Reference)가 일어나서 인자로 참조 변수가 그대로 넘어간다 그래서 값의 수정이 일어나는 경우 원본에도 변화가 생긴다

```
var a = 100;
var objA = { value: 100};

function changeArg(num, obj) {
	num = 200;
	obj.value = 200;
}
changeArg(a, objA);

console.log(a); // 100
console.log(objA); // { value: 200 };
```



