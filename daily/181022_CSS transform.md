# 181022 TIL (CSS transform)

트랜스폼(Transform)은 요소에 이동(translate), 회전(rotate), 확대축소(scale), 비틀기(skew) 효과를 줄 수 있다

다만 트랜지션이나 애니메이션과 같은 효과는 없어서 바로 구현된다

물론 트랜지션이나 애니메이션을 이용한다면 멋진 효과를 낼 수 있다

학원에서 들은 것인데 transform 성능이 좋아서 layout을 정렬할 때에 트랜스폼의 이동(translate)을 이용한다면 좋다고 한다

다 살펴보기 보다는 일단은 많이 쓸 것 같은 요소들만 정리하도록 하겠다

우선 2D와 3D로 나누어진다 3D는 말그대로 3D z축까지를 사용한다

### 1. 2D 트랜스폼

#### 1.1 변환 함수

- translate(x,y): 요소의 위치를 X축으로 x만큼, Y축으로 y만큼 이동시킨다
- scale(x, y): 요소의 위치를 X축으로 x배, Y축으로 y배만큼 확대시킨다
- skew(x-angle,y-angle): 요소를 X축으로 x 각도만큼, Y축으로 y 각도만큼 기울인다
- rotate(angle): 요소를 angle만큼 회전시킨다

#### 1.2 transform

변환함수를 프로퍼티값으로 쉼표 없이 나열한다

나열한 순서대로 효과가 나타난다

ex) transform: translate(10px, 50px) scale(0.55) skew(5deg, -20deg) rotate(70deg)

#### 1.3 transform-origin

요소의 기본기준점을 설정할 때 사용된다

기본기준점은 요소의 정중앙이다(50%,50%). 이동은 기준점을 변경하여도 일정 거리만큼 이동하므로 의미가 없다. 설정값으로 %, px, top left, bottom right을 사용할 수 있다. 0, 0은 top left, 100% 100%는 bottom right과 같은 값이다.



### Comment

마침 배민찬을 하는데 가져온 이미지 작아서  고민이었는데

```css
// div
overflow: hidden

// div img
transform: scale(1.1)
```

위와 같이 해서 깔끔하게 해결하였다