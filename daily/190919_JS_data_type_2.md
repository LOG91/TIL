## 190919TIL (JS 데이터타입과 연산자)

### JS 공부 꾸준히 해야함을 느낌

JS책을 오랜만에 보는데 익숙했던 JS의 특징들이 조금 낯설게 다가온다

JS에 익숙해지기 전까지는 꾸준히 반복해야 함을 느낀다 ㅠㅠ

### Array와 Object 그리고 Prototype

모든 자바스크립트 객체는 prototype을 갖는다

그것은 객체가 생성될 때 결정된다

prototype은 JS에 공식적으로 없는 상속 기능을 가능하게 해준다

prototype chaining을 통해서 가능한데 현재 내 객체에 없는 프로퍼티를 내가 참조하고 있는

prototype에 있다면 그것을 사용할 수 있게 되는 것이다

크롬 개발자도구를 보면 `__propt__`속성이 있는데 그것이 내 객체가 어떤 prototype을 참조하고

있는지 알려준다

### toString()

```
const obj = {name: 'whale'};
obj.toString();
```

obj 객체에 없는 toString()을 사용했지만 가능한 이유는

obj의 __proto__가 Object.prototype을 가리키고 그 안에 toString메서드가 있기 때문에

가능한 것이다

```
const arr = [1,2,3];
const obj = {name: 'whale'};
```

arr는 Array.prototype을 가리키고 obj는 Object.prototype을 가리킨다

하지만 arr.toString() 역시 가능하다 그 이유는 Array.prototype의 프로토타입이

Object.prototype을 가리키기 때문이다

모든 객체의 최상위 프로토타입은 Object.prototype이다 고로 모든 객체는 toString()이 사용 가능하다!



### 🐳오늘의 회고

프로젝트를 오랜만에 오랜 시간 (2시간 30분😨) 붙들고 했다

멈춰 있던 엔진을 돌린 느낌이다 기분이 좋았지만 막막할 때는 뛰쳐나가고 싶었다

매일 코딩은 놓치지 말고 해야 겠다

주여 도와주시옵소서...

이제 사역하러 간다 성령의 불로...!^^