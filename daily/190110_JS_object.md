# 190110 TIL (JS Object)

### 객체 생성방법

- 객체 리터럴을 사용
  타 언어에 비해 매우 간단하게 중괄호`{}`만을 이용해 생성할 수 있다
- Object 생성자 함수

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
