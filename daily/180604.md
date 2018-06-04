## 180604 TIL

#### 1. ArrayParser

반대조건을 체크해서 return 시키고 if분기문 제거하기 (depth 줄이기)

**Old Code**

```js
addValue(context) {
    if (!context.arrayOpen && !context.objectOpen) {
      let processed = this.syntaxChecker.removeLastComma(context.chunk).trim();
      if (this.syntaxChecker.isNumber(processed)) {
        context.completeObj[context.temp] = parseInt(processed);
      } else if (processed.length) {
        this.syntaxChecker.checkError(processed);
        processed = this.syntaxChecker.removeSideQuote(processed);
        processed = this.syntaxChecker.changeToNullAndBoolean(processed);
        context.completeObj[context.temp] = processed;
      }
      context.temp = '';
      context.chunk = '';
    }
  }
```

**New Code**

```js
addValue(context) {
    if(context.arrayOpen || context.objectOpen)return;
      let processed = this.syntaxChecker.removeLastComma(context.chunk).trim();
      if (this.syntaxChecker.isNumber(processed)) {
        context.completeObj[context.temp] = parseInt(processed);
      } else if (processed.length) {
        this.syntaxChecker.checkError(processed);
        processed = this.syntaxChecker.removeSideQuote(processed);
        processed = this.syntaxChecker.changeToNullAndBoolean(processed);
        context.completeObj[context.temp] = processed;
      }
      context.temp = '';
      context.chunk = '';
  }
```

위 코드를 아래와 같이 반대 상황에 리턴을 해주고 나머지 상황은 if분기문을 제거한 채 코드를 실행할 수 있다

#### 2. Leet Code

**My solution**

```js
var twoSum = function (nums, target) {
  for (let i = 0; i < nums.length; i++) {
    for (let j = 0; j < nums.length; j++) {
      if (i === j) continue;
      if (nums[i] + nums[j] === target) return [i, j];
    }
  }
};
console.log(twoSum([2, 7, 11, 14], 9));
```

**Best Practices**

```js
var twoSum = function(nums, target) {
    let hash = {};
    for (let i=0; i<nums.length; i++) {

        let el = nums[i];        
        
        let complementIndex = hash[target - el];

        if (typeof complementIndex !== 'undefined') {
            return [complementIndex, i];
        }
        
        hash[el] = i;
    }
    return null;
};
```

easy의 간단한 문제를 풀었는데 그것의 best practices에서 새로운 세계를 발견할 수 있었다

문제는 nums에 숫자로 구성된 배열, target에 찾고 싶은 값이 input된다

nums의 원소와 원소를 더해서 target값이 된다면 그 두 수의 index를 반환하면 되는 알고리즘 문제였다 중첩을 사용하면 솔직히 바로 답이 나오는 문제이긴 했다

그래서 그렇게 풀었고……(시간이 없어서 오늘은) Best가 뭔지나 보자하고 봤는데 나로서는 우와 이런 방법도 있구나…상태가 오게 됐다

무조건 중첩아니면 안된다고 생각하는 것들에 다 방법이 있다는 것을 다시 깨달았고 객체를 이용한다면 꽤 많은 일들을 할 수 있다는 사실을 알았다

객체를 잘 이용하자!!!



### 회고

오늘 크게 무언가를 한 기억이 없다...

단지 알고리즘 스터디를 하며 스터디 사람들의 생각들을 듣는 것들이 도움이 된 하루였다

코드스쿼드에서 하면서 시간이 무한정이라는 생각에 사로잡히면 안일하게 배우는 것 없이 지나감을 느꼈고 느끼는 사람이 또 있다는 사실을 알았다

셀프 탠션을 주기 위해 새로운 시도를 생각해볼 예정이다





