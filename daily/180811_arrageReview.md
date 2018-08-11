# 180811 TIL (CodeSquad Review 정리)

오늘은 계속해서 미뤄왔던 지금껏 코드스쿼드 렉쳐를 진행하면서 받은 리뷰들을

정리하는 시간을 가지려고 한다 순서는 ArrayParser와 WebVendingMachine만

일단 해봤다 (리뷰 받은 순서대로라 내용의 연계성은 없다)

굳이 작성하지 않아도 잘 고쳐진 부분은 담지 않았다

#### 효과적인 if문 활용

```js
if(this.count === 0){
    fn...
}
// 위 보다는 아래로 구현하는 편이 낫다
if(this.count !== 0) return;
    fn...
```

 #### Commit로그를 달 때

first: 어쩌고 저쩌고.. 는 별 의미가 없다

조금 더 자세하게 feature(하나의 기능, 즉 함수단위)별로 커밋하고 설명을 추가해야 한다!

#### 효과적인 조건문 처리

```js
if(str === 'null')return 'null';
if(str === 'true')return 'true';
if(str === 'null')return 'null';
//위를 아래와 같이 할 수 있다
if(['null', 'true','false'].indexOf(str) > -1) return str;
```

#### Constructor를 이용하여 명시

```js
class DataStructure {
  constructor(syntaxChecker) {
    this.syntaxChecker = syntaxChecker;
    this.arrayParser = new ArrayParser(this, syntaxChecker);
  }
}
// 위처럼 하기 보다 아래처럼 하여 생성할 때 무엇을 받아오는지 명시적으로 해주는 것이 좋다
const arrayParser = new ArrayParser();
const ds = new DataStructure(arrayParser);
```

#### 조건문 안에 코드가 뭘 체크하는지 함수로 만드는 것이 좋다

```js
 if (!parsedData.objectCount && !parsedData.arrayOpen && parsedData.objectOpen) {
     ...
 }
```

파서를 만들면서 이렇게 자주 만들었는데 이렇게 만들면 작성자만 무슨 일을 하는지 알 수 있고 다른 사람은 무엇을 체크하는 코드인지 알기가 어렵다

조건문 안에 함수로 만드는 편이 낫다

#### 반대조건을 체크해 return함으로 분기문을 줄이는 게 좋다

```js
if (!context.arrayOpen && !context.objectOpen) {...}
```

제목이 곧 내용

#### class의 속성 값을 직접 접근해서 가져오기보다 함수를 이용!

```js
this.initWallet(this.walletModel.wallet);
// 위처럼 직접 접근하기보다는 아래처럼 함수를 이용해서 가져오는 것이 좋다!
this.initWallet(this.walletModel.getWalletData());
```

#### 모든 클래스 상단에 주석으로 역할을 1-2줄이라도 표현하는 것이 좋다!