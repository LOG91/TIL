# 프로토타입 (Prototype)
Javascript는 프로토타입 기반 언어라고 불린다 그만큼 자바스크립트에서 중요한 것이 프로토타입의 개념이다

### Prototype vs Class
객체지향언어인 Java, Python, Ruby에서 빠질 수 없는 개념이 Class이다.  
중요한 것은 Javascript도 객체지향언어라는 것이다  
하지만 Javascript에는 클래스라는 것이 없고 프로토타입이 존재한다  

ECMA6표준에서 Claa 문법이 추가되긴 했지만 문법이 추가됐다는 것이지,  
자바스크립트가 클래스 기반으로 바뀌었다는 것은 아니다  
  
### 프로토타입 기반 생성
모든 객체는 프로토타입을 기반으로 하며 프로토타입은 객체에 기본적인 프로퍼티 집합을 부여한다  
프로토타입은 Object 생성자와 연관돼 있으며, 따라서 모든 객체에서 공유한다
```
function Rabbit (adjective) {
  this.adjective = adjective;
  this.speak = function (line) {
    console.log(this.adjective + '토끼가 말합니다 : ' + line);
  };
}

var killerRabbit = new Rabbit("킬러");
killerRabbit.speak("으하하하");
```
토끼 객체는 Rabbit 생성자와 연관된 프로토타입을 기반으로 한다. 생성자의 prototype 프로퍼티를 이용하면  
이 프로토 타입에 접근할 수 있다  
토끼 프로토타입 자체는 객체이므로 Object 프로토타입을 기반으로 하며, Object 프로토타입의 toString메소드를  
공유한다. 따라서 Rabbit 생성자로 생성한 모든 토끼는 이 메소드를 갖게 된다
  
정확한 규칙은 이렇다. 프로토타입의 값을 조회할 때 자바스크립트는 먼저 객체 자체가 갖고 있는  
프로퍼티를 살핀다. 찾고자 하는 이름의 프로퍼티가 있으면 그 값을 취한다.  
아무런 프로퍼티도 없으면 계속해서 해당 객체의 프로토타입, 그리고 그 프로토타입의 프로토타입을  
검색하는 식으로 진행한다. 아무런 프로퍼티를 찾을 수 없으면 undefined값이 반환된다.