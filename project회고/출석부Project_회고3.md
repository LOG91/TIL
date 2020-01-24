# 출석부 Project 회고3

### api 에러

로컬에서 작업하던 것을 aws서버에도 적용을 하는데 특정 api만

계속해서 에러가 났다 치명적 에러라고 생각했지만 아주 간단한 문제였다

번들링만 다시 해주면 해결되는 문제였다...

WDS를 벗어난 변경사항을 늘 고려해두어서 시간 낭비를 절약하자..✔️

### 반응형 개발

반응형 개발이 귀찮게만 느껴졌는데 나름대로의 컨벤션을 정하고

적용하면 막 어려운 일이 아니라고 느꼈다 (잘 되니 나름대로 재미있다)

태그마다 일일이 밑에다가 달아주는 것보다는!

```scss
.header {
  font-size: 3rem;
  .blah {
    width: 30px;
    &__input {
      font-size: 2rem;
    }
    &__button {
      font-size: 2rem;
    }
  }
}

@media screen and (max-width: 768px) {
   .header {
     1rem;
     .blah {
       width: 10px;
      &__button {
        font-size: 1rem;
      }
    }
  }
}
```
위처럼 전체를 복사해주고 변경이 필요한 부분을 작성해주는 것이

지금 나에게는 편한 것 같다 이 부분은 다른 사람들의 코드를 보고 더 좋은 쪽을

찾는다면 바꿀 예정이다