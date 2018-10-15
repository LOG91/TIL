## CyclicRotation
A zero-indexed array A consisting of N integers is given. Rotation of the array means that each element is shifted right by one index, and the last element of the array is moved to the first place. For example, the rotation of array A = [3, 8, 9, 7, 6] is [6, 3, 8, 9, 7] (elements are shifted right by one index and 6 is moved to the first place).

The goal is to rotate array A K times; that is, each element of A will be shifted to the right K times.

Write a function:
> function solution(A, K);

that, given a zero-indexed array A consisting of N integers and an integer K, returns the array A rotated K times.

For example, given
> A = [3, 8, 9, 7, 6]  
> K = 3

the function should return [9, 7, 6, 3, 8]. Three rotations were made:
> [3, 8, 9, 7, 6] -> [6, 3, 8, 9, 7]  
> [6, 3, 8, 9, 7] -> [7, 6, 3, 8, 9]  
> [7, 6, 3, 8, 9] -> [9, 7, 6, 3, 8]

For another example, given

> A = [0, 0, 0]  
> K = 1

the function should return [0, 0, 0]

Given
> A = [1, 2, 3, 4]  
> K = 4

the function should return [1, 2, 3, 4]

Assume that:
- N and K are integers within the range [0..100];
- each element of array A is an integer within the range [−1,000..1,000].

### MySolution
```js
function solution(A, K) {
 
    while(K>0){
        A = pushElement(A);    
        K-=1;
    }
    function pushElement(arr){
        let len = arr.length;
    let pushed = arr.map(function(v, i, a){
        if(i === 0)return a[len-1];
        return a[i - 1];
    })
      return pushed;
    }
    return A;
}
```
### My Solution 2
```js
function solution(A, K) {
  // write your code in JavaScript (Node.js 8.9.4)
  let number = K % A.length;
  while (number > 0) {
    const last = A.pop();
    A.unshift(last);
    number--;
  }
  return A;
}
```

### Comment
코딩 안될 때 휴식이 필요한 것 같다 1시간을 해도 안되던게 나중에 하니 10분 안에 가능했다

### Comment2
- 예전 코드를 보니 가관이었다  
- 예전에 비해서는 확실히 나아짐을 느낀다
- 쉬운 것으로 다시 해보니 할만한다.......