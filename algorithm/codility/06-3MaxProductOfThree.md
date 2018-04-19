# Max Product Of Three
## Task description
A non-empty array A consisting of N integers is given. The product of triplet (P, Q, R) equates to A[P] * A[Q] * A[R] (0 ≤ P < Q < R < N).

For example, array A such that:

  A[0] = -3
  A[1] = 1
  A[2] = 2
  A[3] = -2
  A[4] = 5
  A[5] = 6
contains the following example triplets:

(0, 1, 2), product is −3 * 1 * 2 = −6
(1, 2, 4), product is 1 * 2 * 5 = 10
(2, 4, 5), product is 2 * 5 * 6 = 60
Your goal is to find the maximal product of any triplet.

Write a function:

function solution(A);

that, given a non-empty array A, returns the value of the maximal product of any triplet.

For example, given array A such that:

  A[0] = -3
  A[1] = 1
  A[2] = 2
  A[3] = -2
  A[4] = 5
  A[5] = 6
the function should return 60, as the product of triplet (2, 4, 5) is maximal.

Assume that:

N is an integer within the range [3..100,000];
each element of array A is an integer within the range [−1,000..1,000].
Complexity:

expected worst-case time complexity is O(N*log(N));
expected worst-case space complexity is O(1), beyond input storage (not counting the storage required for input arguments).  
## My solution
```js
function solution(A) {
    // write your code in JavaScript (Node.js 8.9.4)
    let sorted = A.sort((a,b)=>Math.abs(b)-Math.abs(a));
    let isNegativeAll = sorted.every(v=>v<0);
    if(isNegativeAll)return sorted[sorted.length-1] * sorted[sorted.length-2] * sorted[sorted.length-3];
    if(sorted[0] * sorted[1] > 0){
        for(let i = 2; i <sorted.length; i++){
            if(sorted[i]>=0)return sorted[0]* sorted[1] *sorted[i];
        }
    }else{
        for(let i = 2; i <sorted.length; i++){
            if(sorted[i]<=0)return sorted[0]* sorted[1] *sorted[i];
            if(i === sorted.length-1){
                return sorted[0] < 0 ? sorted[1] * sorted[2] * sorted[3] : sorted[0] * sorted[2] * sorted[3];
            }
        }
    }
}
```

## Comment
- 풀긴 풀었지만 억지 끼워넣기 식이 조금 많은 것 같다  
스터디에서 배울 때 많이 배워야겠다