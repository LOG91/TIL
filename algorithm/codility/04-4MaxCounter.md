## MaxCounter

You are given N counters, initially set to 0, and you have two possible operations on them:

increase(X) − counter X is increased by 1,
max counter − all counters are set to the maximum value of any counter.
A non-empty zero-indexed array A of M integers is given. This array represents consecutive operations:

if A[K] = X, such that 1 ≤ X ≤ N, then operation K is increase(X),
if A[K] = N + 1 then operation K is max counter.
For example, given integer N = 5 and array A such that:

    A[0] = 3
    A[1] = 4
    A[2] = 4
    A[3] = 6
    A[4] = 1
    A[5] = 4
    A[6] = 4
the values of the counters after each consecutive operation will be:

    (0, 0, 1, 0, 0)
    (0, 0, 1, 1, 0)
    (0, 0, 1, 2, 0)
    (2, 2, 2, 2, 2)
    (3, 2, 2, 2, 2)
    (3, 2, 2, 3, 2)
    (3, 2, 2, 4, 2)
The goal is to calculate the value of every counter after all operations.

Write a function:

function solution(N, A);

that, given an integer N and a non-empty zero-indexed array A consisting of M integers, returns a sequence of integers representing the values of the counters.

The sequence should be returned as:

a structure Results (in C), or
a vector of integers (in C++), or
a record Results (in Pascal), or
an array of integers (in any other programming language).
For example, given:

    A[0] = 3
    A[1] = 4
    A[2] = 4
    A[3] = 6
    A[4] = 1
    A[5] = 4
    A[6] = 4
the function should return [3, 2, 2, 4, 2], as explained above.

Assume that:

N and M are integers within the range [1..100,000];
each element of array A is an integer within the range [1..N + 1].
Complexity:

expected worst-case time complexity is O(N+M);
expected worst-case space complexity is O(N), beyond input storage (not counting the storage required for input arguments).

### My Solution
```js
// 77%
function solution(N, A) {
  N = Array(N).fill(0);
  return A.reduce((ac, cv) => {
    if (cv === N.length + 1) {
      ac.fill(Math.max(...ac));
    } else {
      ac[cv - 1]++;
    }
    return ac;
  }, N)
}

// 100%
function solution(N, A) {
  let temp, max = 0;
  return A.map(v => v - 1).reduce((ac, cv) => {
    if (cv === N) temp = max;
    else {
      ac[cv] <= temp ? ac[cv] = temp + 1 : ac[cv] += 1;
      if (ac[cv] > max) max = ac[cv];
    }
    return ac;
  }, Array(N).fill(0)).map(v => v > temp ? v : temp);
}

console.log(solution(5, [3, 4, 4, 6, 1, 4, 4]));
```
### Comment
끝내 77%까지 풀지 못했고 밑에 식은 다른 분의 것을 참조하여 내가 다시 풀어본 로직이다  
문제를 보고 꽤 쉽구나 생각했지만 시간복잡도에 걸려서 그 문제를 끝내 해결하지 못했다  
사고력이 아직 부족한 것 같은데 스터디를 하며 잘 하시는 분들의 사고력을 배워서 좋은 것 같다