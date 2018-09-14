# 180914 TIL (Lexical Scope)

RubberDuck 스터디에서 Scope & Closure scope를 다시 하게 되었다

우선 Scope는 **범위**라는 뜻이다

오늘은 Lexical Scope에 대하여 공부했다

이것을 잘 알아야 closure를 잘 알 수 있다

Lexical scope는 어휘적 범위 라고 할 수도 있고 정적 범위라고 할 수도 있다

```js
var a = 'whale';
function fn1(){
	console.log(a);    
}
function fn2(){
    var a = 'log91'
    fn1();
}
fn2();
```

위의 코드를 입력하면 콘솔에 log91이 출력될 것이라고 생각할 수 있다

하지만 콘솔은 whale을 출력한다

Lexical scope때문이다

함수의 스코프는 실행될 때가 아닌 선언될 때 정의되기 때문이다

따라서 fn1이 선언될 때에 스코프는 fn1자신과 전역스코프가 된다

fn2와는 아무 관련이 없는 것이다 따라서 fn2안에서 fn1이 호출될 때 a는 자신의 스코프에는 없다는 것을 알고 chaining을 통해 다음 스코프인 전역으로 가보는 것이다

그리고 거기에서 a를 발견하고 그 메모리에 있는 whale을 불러오는 것이다!

실행컨텍스트, 호이스팅, 클로저 모두가 다 관련이 있는 것이다!!!

이제야 조금씩 뭐가 뭔지 알겠는데 이것을 제대로 설명하라고 하면 설명하기엔 아직 부족할 듯 하다 ㅠㅠ. 오늘은 여기까지!

