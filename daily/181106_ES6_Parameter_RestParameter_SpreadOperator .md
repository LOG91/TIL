# 181106 TIL (ES6 Parameter, Rest Parameter, Spread 연산자)

Spread 연산자… 코드스쿼드 초기에 많이 썼었던 것 같은데 정말 오랜만에 본 것 같다

다시 공부하면서 보니 너무 혁신적이다!

slice()를 써서 복사를 할 필요도 없다는 게 컸다

### 1. 파라미터 기본값

ES5에서는 파라미터에 기본값을 설정해줄 수 없어서 들어오는 인수를 체크해서 해결했다

```js
function add(a, b){
    a = a || 0;
    b = b || 0;
    return a + b;
}

console.log(add()); // 0
console.log(add(2,3)); // 5
```

하지만 ES6에서는 값이 할당되지 않았을 때의 값을 파라미터에 설정해줄 수 있다

```js
function add(a = 1, b = 1){
    return a + b;
}
console.log(add()); // 2
console.log(add(3)); // 4
console.log(add(3,4)); // 7

// 참고로 undefined를 직접 넣어줘도 동작한다 add(2,undefined) = 3
// null, [], 0, false ... 과 같은 어떤 값도 안된다
```

### 2. Rest 파라미터

#### 2.1 사용

Rest파라미터는 Spread연산자(…)를 사용하여 파라미터를 정의하는 것을 말한다

rest파라미터와 spread연산자가 헷갈렸는데 이번에 알게 되었다

spread연산자는 말그대로 연산자여서 (…)의 형태의 연산자를 말한다

rest 파라미터는 그 연산자를 사용해서 파라미터에 사용하는 것을 말한다

rest 파라미터를 사용하면 여러가지 인수를 함수 내부의 배열로 전달받을 수 있다

```js
function foo(...rest){
    console.log(rest);
}
foo(1,2,3,4,5); // [1,2,3,4,5]
```

인수는 순차적으로 파라미터와 rest파라미터에 할당된다

```js
function foo(param, ...rest){
    console.log(param);
    console.log(rest);
}

foo(1,2,3,4,5);
// 1
// [2,3,4,5]
```

중요한 것은 rest미터는 반드시 마지막으로 파라미터여야 한다!

```js
function foo(...rest, param){
    console.log(rest);
    console.log(param);
}
foo(1,2,3,4,5); // SyntaxError: Rest parameter must be last formal parameter
```

#### 2.2 arguments의 극복

ES5에서는 함수에 인자가 가변으로 들어오게 될 경우 arguments를 통해 개수를 파악할 수 있고 이를 통하여서 가변되는 인수들을 처리했었다

문제는 arguments가 유사 배열인 객체로 들어오기 때문에 함수 메소드를 사용할 수 없다

하지만 rest 파라미터를 이용하면 가능하다

```js
function foo(...rest){
    return rest.reduce((ac,cv){
        return ac+cv;
    },0);
}
```

또 화살표 함수에는 arguments프로퍼티가 없기에 반드시 rest를 사용해야 한다!

### 3. Spread 연산자

```js
function foo(a,b,c){
    console.log(a,b,c);
}

const arr = [1,2,3];
foo(...arr); // 1 2 3
```

spread 연산자는 위와 같이 배열을 펼쳐서 인수로 들어가게 한다

rest 파라미터와 비슷하니 혼동을 주의해야 한다!

spread연산자는 배열에서 사용될 때 그 기능이 꽃을 피운다!

몇 가지 사용 예를 들어보겠다

#### 3.1 배열에서 사용

##### 3.2.1 concat

```js
const arr = [1,2,3];
console.log([...arr, 4, 5, 6]); // [1, 2, 3, 4, 5, 6]
```

##### 3.2.2 push

```js
const arr1 = [1,2,3];
const arr2 = [4,5,6];
arr1.push(...arr2);
console.log(arr1); // [1,2,3,4,5,6]
```

##### 3.2.3 splice

```js
const arr1 = [1,2,3,6];
const arr2 = [4,5];

arr1.splice(3,0,...arr2);
console.log(arr1); //[1,2,3,4,5,6];
```

##### 3.2.5 copy

```js
// ES5
var arr = [1,2,3];
var copy = arr.slice();

//ES6
const arr = [1,2,3];
const copy = [...arr];
```



#### 3.2 객체에서의 사용

spread 연산자를 사용하면 객체를 손쉡게 병합 또는 변경할 수 있다

```js
// 객체의 병합
const merged = {...{x:1,y:2}, ...{y:10,z:3}};
console.log(merged); // {x:1, y:10, z:3}

// 특정 프로퍼티 변경
const changed = { ...{ x: 1, y: 2 }, y: 100 };
// changed = { ...{ x: 1, y: 2 }, ...{ y: 100 } }
console.log(changed); // { x: 1, y: 100 }

// 프로퍼티 추가
const added = { ...{ x: 1, y: 2 }, z: 0 };
// added = { ...{ x: 1, y: 2 }, ...{ z: 0 } }
console.log(added); // { x: 1, y: 2, z: 0 }
```

spread 연산자를 사용하면 위에서 arguments를 배열로 변환한 것처럼 유사 배열 객체를 배열로 손쉽게 변환 가능하다!

```js
const htmlCollection = documents.getElementsBytagName('li');

const newArray = [...htmlCollection];

// ES6의 Array.from 메소드를 사용해서도 가능하다
// const newArray = Array.from(htmlCollection);
```



## Reference

**Poiema Web**