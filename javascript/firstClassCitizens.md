# First Class Citizens

### First Class Citizens

first class citizen이란 자유롭게 거주하고 일 할 수 있고, 출입국의 자유를 가지며, 투표의 자유를 가지는 시민을 의미한다  프로그래밍에서 1급 객체라고 하는 것은 type을 전달, 반환 및 할당할 수 있음을 말한다

자바스크립트는 함수가 1급 객체라는 중요한 특성이 있다

1급 객체의 조건

- 변수나 데이터 구조 안에 담을 수 있다
- 파라미터로 전달할 수 있다
- 반환값으로 사용할 수 있다
- 동적으로 프로퍼티를 할당할 수 있다

#### 1.변수에 할당

```js
const log = function(name){console.log('Hello ' + name)}
log('whale'); // Hello whale
```

#### 2.파라미터로 전달

```js
const log = function(name){console.log('Hello ' + name)}
function func(fn){return fn('log91')}
func(log); // Hello log91
```

#### 3. 반환값으로 사용

```js
const log = function(name){
    function fn(name){console.log('Hello ' + name)}
    return fn;
}
const hi = log();
hi('killerWhale'); // Hello killerWhale
```