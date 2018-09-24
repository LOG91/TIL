# 180924 TIL (CSS position)

이 글은 poiemaweb을 참조하여 작성되었습니다

## Position 프로퍼티

Position은 요소의 위치를 정의한다

그동안 relative와 absolute를 사용해서 해야 한다고 이야기만 듣고 모르고 사용하다보니

정말 답답했는데 이번에 공부하면서 어떤 방식인지 이해하게 되었다

마크업은 가볍게 생각하고 쓸 때만 찾아보는 것이 아니라 공부해야 함이 확실하다..!

position에는 static, relative, absolute, fixed가 있다

### 1. static

static은 position의 default값이다

기본적인 요소의 배치 순서에 따라 위에서 아래로, 왼쪽에서 오른쪽으로 순서에 따라 배치된다

부모 요소 내에 자식 요소로서 존재할 때는 부모 요소의 위치를 기준으로 배치된다!

평소에 사용할 일은 없지만 이미 지정된 position을 무력화하기 위해 사용할 수 있다

좌표 프로퍼티(top, bottom, left, right)와 같이 사용할 수 없다

### 2. relative

기본 위치를 기준으로 좌표 프로퍼티를 사용하여 이동시킨다

static을 선언한 요소와 relative를 선언한 요소의 차이점은 좌표 프로퍼티의 동작 여부 뿐이며 그 외에는 동일하게 동작한다!

### 3. absolute

부모 요소 또는 가장 가까이 있는 조상 요소(static제외)를 기준으로 좌표 프로퍼티만큼 이동한다

즉 relative, absolute, fixed 프로퍼티가 선언되어 있는 부모 또는 조상 요소를 기준으로 위치가 결정된다

만일 부모 또는 조상 요소가 static인 경우 document body를 기준하여 좌표 프로퍼티대로 위치하게 된다

따라서 부모 요소를 배치의 기준으로 삼기 위해선 부모 요소를 relative로 정의해야 한다

**이 때 다른 요소가 먼저 위치를 점유하고 있어도 뒤로 밀리지 않고 덮어쓰게 된다**

이런 특성을 부유 또는 부유 객체라고 한다

absolute 선언 시, block레벨 요소의 width는 inline 요소와 같이 content에 맞게 변화되므로 적절한 width을 지정해야 한다!

> relative와의 차이점
> absolute는 부모에 static이외의 position프로퍼티가 지정되어 있을 경우에만 부모를 기준으로 배치가 가능하다 조상이 모두 static이라면 body를 기준으로 위치한다
> 따라서 absolute프로퍼티는 부모 요소의 영역을 벗어나 어디든 자유롭게 위치가능하다!

### 4. fixed

부모 요소와 관계 없이 브라우저의 viewport를 기준으로 좌표프로퍼티를 사용하여 위치를 이동시킨다

스크롤이 되더라도 화면에서 사라지지 않고 항상 같은 곳에 위치한다!

