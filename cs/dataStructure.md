# Data Structure (자료구조)

오늘은 자료구조에 대하여 다룬다

두서 없는 순서로 우선 작성해보려고 한다

자료구조의 필요성을 아직 느끼지 못할 정도로 내 개벌의 수준이 낮지만 지금 보니

왜 필요한지, 왜 이해해하고 있어야 하는지 알겠다

먼저 가장 간단한 Stack & Queue부터 살펴보재이!

### Stack & Queue

자료구조에서 어찌보면 가장 이해하기 쉬운 개념이다

Stack은 LIFO, Queue는 LILO의 구조를 갖고 있다

각각 last in first out (후입선출), last in last out 혹은 first in first out(선입선출)을 뜻하며

LIFO는 마지막 들어간 데이터가 제일 처음 나오는 구조, LILO 혹은 FIFO는

들어간 순서대로 나올 수 있다

#### Stack

폐쇄공포증을 유발할 수도 있지만 앞 문이 없고, 들어간 사람이 먼저 나올 수 없는 폭의 장소라고 설명할 수 있다

그러면 가장 뒤에 사람부터 나올 수 밖에 없기 때문이다

스택은 가깝게 콜스택을 예로 들 수 있다

함수 호출에 따라 콜스택에 함수가 쌓여간다

그리고 나중에 들어간 함수가 리턴되기 전까지 그 전에 들어간 함수들은 나올 수 없다

물론 비동기 호출에서는 가능하다고도 할 수 있다

PUSH를 이용하여 스택을 쌓을 수도 있고, POP을 이용하여 맨 위의 자료를 제거할 수도 있다

재귀를 무한대로 호출하다보면 스택오버플로우 에러를 만날 수 있는데 스택이 계속해서 쌓여가 메모리가

견디지 못한 것이다

사용되는 예는 브라우저의 뒤로가기, 실행 취소 등이 있겠다

#### Queue

반대되는 자료구조라고 볼 수 있다

먼저 들어간 순서대로 빠져나올 수 있는 구조다 은행창구처럼말이다

먼저 시작한 작업이 꼭 먼저 끝남을 보장 받아야 하는 작업을 할 때 사용하면 된다

음.. 예를 들면 나이키에서 드로우를 할 때 대기열이나 수강신청할 때 대기열이 될 수 있겠다