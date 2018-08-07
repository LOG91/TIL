# 180802 Offline

## 1. Symbol

javascript Primitive type

js에는 5개가 있다 (string, number, boolean, null, undefined)

값 자체를 가지고 비교를 함.

immutalble 한 속성

### Symbol의 선언

Description string을 넣어서 선언할 수 있다 (생략가능)

## 2. Iteration

### String, Array, Set, Map, NodeList

```js
const str = 'codesquad';
const arr = ['code', 'squad'];
const setData = new Set(['code','squad']);
const mapData = new Map([['first', 'code'],['second','squad']]);
```

#### for-of로 iteration

String, Array, Set, Map, NodeList는 for-of를 사용할 수 있다

```js
for(let v of str) {
    console.log(v);
}
for(let v of arr) {
    console.log(v);
}
for(let v of setData) {
    console.log(v);
}
for(let [k,v] of mapData) {
    console.log(k, v);
}
```

#### for-of가 되는 것은 spread operator를 이용해 펼칠 수 있다

### object iteration

```js
const obj = {first:'whale',second:'squad'};
for(value of obj){
    console.log(value); // Uncaught TypeError: obj is not iterable
}
```

#### iterable protocols이란?

모든 object에 적용할 수 있는 iterable protocol과 iterator protocol 두 개가 ES2015에 추가됨.

For-of 를 사용할 수 있다면 iterable을 구현한 것임.

stirng, array, set, map은 for...of를 사용할 수 있고, build-in iterables이다.

다시 말해 iterable protocol을 따르고 있다.

### iterable protocols - Symbol.iterator란?

어떤 객체가 iterable하기 위해서는 Symbol.iterator 'key'속성이 있으면 된다.

```js
const str = 'codesquad';
typeof str[Symbol.iterator]; // function

const obj = {};
typeof str[Symbol.iterator]; // undefined
```

Array도 마찬가지로 Symbol.iterator 함수가 있음.

```js
const arr = ['code', 'squad'];
typeof arr[Symbol.iterator];
```

### custom iterable 객체 만들기

- 객체에 Symbol.iterator를 추가한다
- Next 속성을 갖는 객체를 만들고

### Generator

Generator함수는 iterator를 쉽게 만들 수 있게 한다

즉, iterator

```js
class DoubleMaker {
    constructor(data){
        this.data = data;
    }
    * myGenerator() {
        let idx = 0;
        while(true){
            yield Math.pow(this.data[idx++],2);
            if(idx >= this.data.length) break;
        }
    }
}

const dbl = new DoubleMaker([1,2,3,4,5]);
const dblGenerator = dbl.myGenerator();
dblGenerator.next().value; //1
dblGenerator.next().value; //4
dblGenerator.next().value; //9
```



새로운 자료구조가 나올 때마다 iterate할 표준이 필요했기에 Symbol.iterator를 만들게 되었고 next()가 가능하게 만들었다