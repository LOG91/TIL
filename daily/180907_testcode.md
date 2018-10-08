# 180907 TIL (TestCode)

2주간 아프로 1주간 회복하느라 오랜만에 쓰는 TIL이다

사실 더 일찍 코딩할 수 있었지만 나에게 쉬는 시간을 허락했던 것 같다

Github에 숲이 사라져가는 것을 본 순간 마음이 아팠다

보여주기 식은 좋지 않지만 그래도 TIL을 함으로써 내가 얻는 것들이 많은 것 같다

글을 잘 쓰고 싶은데 이것으로 계속 훈련이 되는 것 같다

블로그도 해보고 싶은데 영어공부의 소중함을 느껴 영어에 많이 투자하게 되어 여유가 없다..ㅠ



오늘은 코드스쿼드에서 웹 자판기 마지막 TestCode리뷰를 중심으로 공부했다

마스터의 리뷰를 중심으로 쓴 TestCode에서 중요한 것은 이것이다

- mock을 너무 많이 쓰지 않는 것이 좋다 (어렵지만 실제 UI 변화를 테스트하기 때문)
- 테스트코드도 실제와 동일하다 그러므로 전역공간의 것을 같이 쓰는 것 좋지 않다
- 무엇을 테스트해야할까 라는 궁금증이 있다면 ''이 함수는 이렇게 동작되어야 해!'' 라는 부분을 테스트하면 된다

- 비슷한 test 들을 그룹핑할때 describe메서드를 활영한다 네임스페이스의 역할이라고 보면 된다

#### Comment

- 테스트코드 어려운 것 같다 무엇보다 Jest에 관한 정보가 부족하다
- 테스트코드에도 배워야 할 게 꽤 많은 것 같은데 너무 깊게 하기보다는 적당히 하고 일단은 넘어가는 것이 좋겠다..