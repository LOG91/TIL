# 180913 TIL (TestCode Review)

두 달간의 Web Vending Machine 스텝이 끝이 났다

마지막으로 마스터님께서 해주신 테스트코드 리뷰를 TIL로 정리하고 마무리하려고 한다

### 개선해야할 점

#### Normal

template 모듈을 Temp라는 변수로 모듈화했는데 Temp는 프로그래밍에서 임시의 뜻으로 많이 쓰이기 때문에 좋지 않다 template, tpl이 적당하다

#### Testcode

- 테스트코드도 유지보수를 해야 한다 그래서 그것을 고려하며 짜야 한다

- 테스트함수간에 상태 공유를 최소화 해야 한다, UI가 변경될 때 여러 부분을 수정해줘야 한다면 좋은 코드가 아닌 것이다

- "해당 번호의 아이템이 올바른 node로 랜더링됐다" 라는 표현은 모호하다
  -> "해당 번호의 아이템이 지정해준 template으로 랜더링됐다"로 바꾸어 봤다

- 하드코딩 되어있는 expected 값을 계산을 통함으로 값 변경을 대처한다

  ```js
  test('투입한 금액으로 살 수 있는 상품이 하이라이트된다', () => {
          const TOTAL_INSERTED_MONEY = 700;
          machineView.renderMachine(testItems);
      	const expected = 3; 
          const expected = testItems.reduce((ac, cv) => {
            if (cv.price <= TOTAL_INSERTED_MONEY) ac++;
            return ac;
          }, 0); // 700원 아래의 Item 3개
  
          machineView.renderAvailableItem(TOTAL_INSERTED_MONEY);
  
          expect(document.querySelectorAll('.available_item').length).toBe(expected);
        });
  ```

- **beforeEach가 꼭 필요한 것은 아니다 공통적으로 test함수에 앞서서 필요한 것들만 추출하는 것이고 가급적 given/when/then을 따라 test안에 상황을 정의해두는 것이 좋다!**

