## Find middle element

```
As a part of this Kata, you need to create a function that when provided with a triplet, 
returns the index of the numerical element that lies between the other two elements.

The input to the function will be an array of three distinct numbers (Haskell: a tuple).

For example:
```

```js
gimme([2, 3, 1]) => 0
```

```
2 is the number that fits between 1 and 3 and the index of 2 in the input array is 0.

Another example (just to make sure it is clear):
```

```js
gimme([5, 10, 14]) => 1
```

```
10 is the number that fits between 5 and 14 and the index of 10 in the input array is 1.
```

### My solution
```js
var gimme = function (inputArray) {
  var original_arr = [];
  for (var i = 0; i < inputArray.length; i++){
    original_arr.push(inputArray[i]);
  }
  for(var i = 0; i < inputArray.length; i++){
    if(original_arr[i] === inputArray.sort(function(a,b){return a-b;})[1]) return i;
  }
};
```

### Best practices
```js
function gimme(a) {
  return a.indexOf(a.concat().sort(function(a, b) { return a - b })[1])
}
```

### Comment
코딩 능력 차이가 실감되는 것 같다  
적극적으로 함수를 배우고 방식들을 실제로 적용할 수 있도록 해야겠다