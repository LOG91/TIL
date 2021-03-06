# 180719 TIL (MVC 오프라인 수업)

#### MVC는 프로그램 디자인 패턴이다

- Model : 데이터를 처리하는 부분
- View : 화면에 보여지는 부분
- Controller : Model과 View 모두와 연결되어 있고 Commander의 역할을 하는 부분

그냥 프로그램을 짜다보면 처음에는 잘 동작할지 몰라도 유지보수를 함에 있어서

함수 하나를 바꿔도 함수끼리 서로 관여하고 있어서 여러 개의 함수를 수정해야 하고

심하면 어떻게 뭘 바꿔야할지 모르게 되는 치명적인 상황이 오기도 한다

그렇기에 프로그램을 그냥 짜는 것이 아니라 디자인해줘야하는 필요가 생긴다

#### 프로그램을 짤 때 **느슨한 관계**를 만드는 것이 중요하다

모델과 뷰를 분리하는 것에 중점을 둬야 한다

관계를 끊어주는 것이 필요하다 => 한 곳에 모으는 것이 필요하다

곳곳에서 일어나는 변화들을 중앙에서 받고 알려주는 것이다

프로그램의 규모가 커지면 컨트롤러는 더 커진다

그 때에 컨트롤러를 한 개 더 만들어줄 수도 있다



#### 내가 고민해보는 것이 필요하다

그래야지 이것의 장단점을 내 스스로 얘기할 수 있다



#### 주의점

MVC는 자바, C에서 출발한 디자인 패턴이다

그래서 구글링을 하며 JS에 적용해보면 무언가 어색한 경우가 발생하기도 한다

예를 들면 싱글턴 패턴이다 자바스크립트는 이미 싱글턴 패턴이다



#### 짧은 사용 후기

웹자판기를 짜면서 MVC를 적용해보게 되었는데 나름대로 재미가 있다

https://github.com/LOG91/javascript-vm/tree/step4

아직 처음이라 정확히 어떤 필요가 생겨서 어디에 적재적소에 넣어주는 이런 것은 없지만

왜 이런 패턴이 필요한지 조금은 알 것 같다