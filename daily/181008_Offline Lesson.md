# 181008 TIL (Offline Lesson)

## Offline lesson

> outline: 1px solid gray를 이용해 box model 쉽게 볼 수 있음

constructor에서는 객체 뼈대만 만들어주는 느낌이다(속성)

거기서 함수가 실행되는 것은 어색하다

class의 인자를 잘 쓰는 것이 중요하다!

### Single Page

#### app.js (entry point)

- 여기에 관계를 다 보여줘야 한다

- 객체의 초기화만 이루어지는 것이 좋다 detail이 많아서는 안된다
  책을 열었으면 목차가 다 보이는 것과 같다
  구조를 일목요연하게 보여주는 것이 필요한 것이다

- 여기서는 객체 생성만 하는 것이 좋다

- initailize정도까지는 할 수 있지만
  render나 event등록도 하지 않는다

#### 주입받는 쪽에서 메소드의 이름도 모르게 짤 수 있다

예를 들면 아래와 같다

```js
//app.js
const variety = new ContentSlider({
	'GET_DATA' : promotionContentModel.getData();
})
//contentSlider
class ContentSlider {
    constructor(option){
        this.option = option
    }
    showData(){
        currentList = this.option.GET_DATA
        document.body.innerHTML = `<div>${currentList}</div>`
    }
}
```

modules의 의존성을 잘 관리한 후에 배포할 때는 bundle로 배포된다

webpack이 그 예다