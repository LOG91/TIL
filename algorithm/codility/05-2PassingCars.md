## Passing Cars

A non-empty zero-indexed array A consisting of N integers is given. The consecutive elements of array A represent consecutive cars on a road.

Array A contains only 0s and/or 1s:

0 represents a car traveling east,
1 represents a car traveling west.
The goal is to count passing cars. We say that a pair of cars (P, Q), where 0 ≤ P < Q < N, is passing when P is traveling to the east and Q is traveling to the west.

For example, consider array A such that:

  A[0] = 0
  A[1] = 1
  A[2] = 0
  A[3] = 1
  A[4] = 1
We have five pairs of passing cars: (0, 1), (0, 3), (0, 4), (2, 3), (2, 4).

Write a function:

function solution(A);

that, given a non-empty zero-indexed array A of N integers, returns the number of pairs of passing cars.

The function should return −1 if the number of pairs of passing cars exceeds 1,000,000,000.

For example, given:

  A[0] = 0
  A[1] = 1
  A[2] = 0
  A[3] = 1
  A[4] = 1
the function should return 5, as explained above.

Assume that:

N is an integer within the range [1..100,000];
each element of array A is an integer that can have one of the following values: 0, 1.
Complexity:

expected worst-case time complexity is O(N);
expected worst-case space complexity is O(1), beyond input storage (not counting the storage required for input arguments).

### My Solution
```js
function solution(A) {
  let counter = 0;
  let car = A.reduce((ac, cv, idx, a) => {
    if (cv === 0) {
      counter++;
      return ac + (a.length - 1) - idx;
    }
    return ac;
  }, 0);
  counter--;
  let zero = (counter * (counter + 1)) / 2;
  let result = car - zero;
  return result <= 1000000000 ? result : -1;
}
```
URL : https://app.codility.com/demo/results/training6ADXFE-GWE/

### Comment
변수 이름 짓는 것과 직관적이게 로직을 짜는게 부족한 것 같다  
좀 더 아름다운 코드로 만들고 싶지만 오늘은 여기까지...