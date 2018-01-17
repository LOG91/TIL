# 객체 (Object)
### 1. 작성
중괄호 {}를 사용한다
`var cat = {color : "회색", name : "금강", size : 46};`

### 2. 속성 (property)  
위 코드의 color: "회색", name : "금강" 의  값들이 속성이며 콤마(,)로 구분  

### 3. 키(key)와 값(value)  
왼쪽 값(color) 는 key가 되고 오른쪽 값(회색)이 value가 된다  

### 4. 객체 만들기 
객체를 만드는 방법에는 일반적으로 두 가지 방법이 있다  
- 객체 리터럴
```js
// 객체 리터럴을 사용해서 빈 객체를 초기화시킨다.
var cat = {};

var cat = {
color: "회색",
name: "금강",
size: 46,

sound: function () {
console.log("야옹");
}
}
```

- 객체 생성자 (Constructor)  
객체 생성자로 만드는 것이다. 생성자는 새 객체를 초기화하는 함수이며  
생성자를 호출하기 위해 new키워드를 사용한다
```js
var cat =  new Object ();
cat.color = "회색";
cat.name= "금강";
cat.size = 46;

cat.sound = function () {
console.log("야옹");
}
```
객체의 프로퍼티 이름으로 “for”와 같은 몇몇 예약어를 사용할 수 있지만, 피하는 것이 현명하다.
객체는 숫자, 배열과 심지어 다른 객체를 포함하는 모든 데이터 타입을 수용할 수 있다. 

### 5. 프로퍼티에 접근하는 법
객체의 프로퍼티에 접근하는 두 가지 주요 방법은 점 표기법과 대괄호 표기법이다.  
- 점 표기법
```js
// 지금까지의 예제에서 점 표기법을 사용해왔다. 여기 또 하나의 예제가 있다:
var cat = {color: "회색", name: "금강", size:46};

// 점 표기법을 사용해서 cat 객체의 프로퍼티에 접근하려면, 이렇게 한다:
console.log (cat.color); // 회색
console.log (cat.name); // "금강"
```
- 대괄호 표기법
```js
// 대괄호 표기법으로 cat 객체의 프로퍼티에 접근하려면, 이렇게 한다:
console.log (cat["color"]); //회색
console.log (cat["name"]); // "금강"

//혹은, 변수로 프로퍼티 이름을 가질 수도 있다:
var catColor = "color";
console.log (cat[catColor]); // 회색
```