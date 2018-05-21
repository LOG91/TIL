## Build the future of the web with modern Javascript (Google I/O 2018)

2018년 Google I/O에서 발표된 내용이고 크롬 V8엔진 팀에 있는 두 개발자가 나와서 프리젠테이션을 진행했다

최신 자바스크립트의 기술 개요와 Node.js, V8 engine을 이용해 기대할 수 있는 것과 성능 향상과 안정할 수 있는 방법을 다루고 있다

### Javascript is anywhere

"Javascript is anywhere" 이라는 한 마디가 인상깊었다

자바스크립트는 웹의 스크립트언어다

하지만 오늘날에는 웹을 넘어서 사용되는 경우가 많다

예전부터 Javascript를 이용하여 모바일 앱을 개발하고 싶은 생각이 많았어서 더 흥미를 끌고 관심있게 보게 되었다 

이제는 Javascript가 단순히 웹의 스크립트언어가 아니라는 것을 더 확실히 알게 되었다



### Javascript New Syntax

#### 1. Module System

편리한 모듈화

export와 import를 이용하여 const, function을 포함해 어느 값이라도 간단하게 모듈화시킬 수 있다 그리고 파일명을 js가 아닌 mjs를 사용한다

**lib.mjs**

```js
export const name = 'Whale';
export function sayHello(name){
    console.log(`Hello ${name}!`);
}
```

**main.mjs**

```js
import {name, sayHello} from './lib.mjs';
console.log(name);
sayHello(name) 
```

module파일은 일반적인 파일과 구분을 해줘야 한다

```js
<link rel ="modulepreload" href="lib.mjs">
<link rel ="modulepreload" href="main.mjs">
<script type="module" src = "main.mjs"></script>
<script nomodule src="fallback.js"></script>
```

```js
function loadThumbnail(relativePath){
	const url = new URL(relativePath, import.meta.url);
    const img = new Image();
    img.src = url;
    return img
}
const thumbnail = loadThumbnail('../img/googleio.png');
container.append(thumbnail);
```

솔직히 이해가 잘 되지 않았지만 최신버전부터 모듈시스템을 조금 더 간편하게 업그레이드시킨 것 같았다

ArrayParser를 하며 이제 막 module로 분리하는 작업을 시작한 나로서는 공감할 수 없는 내용이었다

#### BigInt()

Javascript의 Max number를 증가시키는 새로운 숫자범위?

트위터 ID와 같은 고유 넘버가 지금까지의 숫자 범위를 넘어서서 필요한 체계가 아닌가 싶다

크롬과 오페라가 지원하고 있고 곧 다른 브라우저에서도 지원될 예정이라고 한다

#### Async iteration

 ```js
async function print(readable){
    readable.setEncoding('utf8');
    let data = '';
    for await (const chunk of readable){
        data +=chunk;
    }
    console.log(data);
}

const fs = require('js');
print(fs.createReadStream('./file.txt'));
 ```

#### RegExp dotAll mode

**1.**

```js
const input = `Lorem ipsum dolor sit amet, sonsecretur hello
world elit. Nam sit amet ......`;

/hello.world/u.test(input);
```

결과는 false다 hello에서 개행했기 때문이다, 그래서 아래와 같은 방법으로 true를 만들어줄 수 있다

```js
/hello[\s\S]world/u.test(input);
/hello[^]world/u.test(input);
```

하지만 이 방법이 복잡하고 힘들기 때문에 이번에 새로운 문법에서 추가된 것이 있다

```js
/hello.world/su.test(input);
```

이렇게 /뒤에 s를 붙이는 방법이다 us로 순서를 바꿔도 상관없다

크롬, 오페라, 노드, 사파리에서 지원한다고 한다

__2.__

```js
const pattern = /(\d{4})-(\d{2})-(\d{2})/u;
const result = pattern.exec('2018-05-09');
// result[0] === '2018-05-09`
// result[1] === '2019'
// result[2] === '05
// result[3] === '09'
```

위와 같이 배열에 할당된다

이렇게 배열로 나눌 수는 있지만 가독성이 떨어진다고 볼 수 있다

그래서 새로운 문법이 나왔다

```js
const pattern = /(?<year>\d{4})-(?<month>\d{2})-(?<day>\d{2})/u;
const result = pattern.exec('2018-05-09');
// result.group.yaer === '2018'
// result.group.month === '05'
// result.group.day === '09'
```

위처럼 나눠진 배열에 이름을 부여해서 객체값을 불러오듯 불러올 수 있게 된 것이다

배열의 숫자보다 훨씬 더 쉽게 원하는 값을 찾을 수 있다

정규표현식 관련해서 더 많은 자료가 있었지만 아직 이해하기가 힘들어서 두 가지 부분만 다뤘는데 정규표현식도 점점 더 쉬워지는 시대가 오지 않을까 생각이 됐다

#### String#trim(Start, End)

```js
const string = '   hello whale  ';
string.trim();
// 'hello whale'
```

기존의 trim메소드는 선택사항 없이 양쪽의 공백을 없애줬다

```js
string.trimStart();
// 'hello whale  '
string.trimEnd();
// '.  hello whale'
```

trim()에 새로운 메소드가 추가됐고 이렇게 시작쪽만 할 것인지 마지막쪽만 할 것인지 정할 수 있다

#### Object rest & spread

```js
const primes = [2,3,5,7,11];
const [first, second, ...rest] = primes;
console.log(first); // 2
console.log(second); // 3
console.log(rest); // [5,7,11]

const primeCopy = [first, second, ...rest];
console.log(primeCopy); // [2,3,5,7,11]
```

```js
const person = {
    firstName : 'Daenerys',
    lastName : 'Targaryen',
    nickName : 'Dany',
    culture : 'Valyrian'
}
const {firstName, lastName, ...rest} = person;
console.log(firstName); // 'Daenrys'
console.log(lastName); // 'Targaryen'
console.log(rest); // {nickName : 'Dany', culture : 'Valyrian'}

const personCopy = {firstName, lastName, ...rest};
// {
//    firstName : 'Daenerys',
//    lastName : 'Targaryen',
//    nickName : 'Dany',
//    culture : 'Valyrian'
// }
```

```js
const data = {x: 42, y: 27, label: 'Treasure'};

// Old
const clone1 = Object.assign({}, data);

// New
const clone2 = {...data}

//{x: 42, y :27, label: 'Treasure'} Either results

const defaultSettings = {logWarnings: false, logErrors: false};
const userSettings = {logErrors: true};

// Old
const settings1 = Object.assign({}, defaultSettings, userSettings);

//New
const settings2 = {...defaultSettings, ...userSettings};
// {logWarnings : false, logErrors : true} Either results
```

rest와 spread와 관련해서는 한 번 배우고 잘 사용하질 않아서 크게 편해진 것에 대하여 공감은 안되지만 대략적으로 어떤 내용인지는 이해했다

크롱의 ES6강의에서 destructuring에서 배웠는데 이 부분을 응용하면 코드가 훨씬 간결해지고 복사도 쉽게 할 수 있을 것 같다

### 느낀점

가장 먼저는 영어공부를 꼭 하고 싶다는 생각을 하게 됐고 영어로 문서들을 보는 것을 실생활화해야함을 가장 많이 느꼈다...

Javascript라는 언어가 문법적으로나 범용성으로나 계속해서 발전하고 있다는 것을 가장 가까이에서 본 것 같다

ES6 강의를 듣고 하지만 실제로 귀찮은 마음에 적용할 생각은 안하고 계속해서 하던대로 코드를 짰는데 실제 코드에 계속해서 적용시키는 연습을 해야할 것 같다





