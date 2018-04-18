# Distinct
Write a function

function solution(A);

that, given a zero-indexed array A consisting of N integers, returns the number of distinct values in array A.

Assume that:

N is an integer within the range [0..100,000];
each element of array A is an integer within the range [−1,000,000..1,000,000].
For example, given array A consisting of six elements such that:

 A[0] = 2    A[1] = 1    A[2] = 1
 A[3] = 2    A[4] = 3    A[5] = 1
the function should return 3, because there are 3 distinct values appearing in array A, namely 1, 2 and 3.

Complexity:

expected worst-case time complexity is O(N*log(N));
expected worst-case space complexity is O(N), beyond input storage (not counting the storage required for input arguments).

## My solution
```js
function solution(A) {
    let set = new Set();
    A.forEach(v=>set.add(v));
    return set.size;
}
```
URL https://app.codility.com/demo/results/trainingW9YDC2-DJP/
## Better solution
```js
function solution(A) {
    // write your code in JavaScript (Node.js 8.9.4)
    return new Set(A).size;
}
```

## Comment
- distinct의 뜻을 알아보는데만 시간이 걸리는 문제다
- 풀고나서 이게 맞나 싶어서 다른 분 꺼 보니까 Better solution처럼 간단히 초기화 가능하다