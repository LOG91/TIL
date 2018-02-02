## Arithmetic

```
Given two numbers and an arithmetic operator (the name of it, as a string), 
return the result of the two numbers having that operator used on them.

a and b will both be positive integers, 
and a will always be the first number in the operation, and b always the second.

The four operators are "add", "subtract", "divide", "multiply".

A few examples:
```

```js
arithmetic(5, 2, "add")      => returns 7
arithmetic(5, 2, "subtract") => returns 3
arithmetic(5, 2, "multiply") => returns 10
arithmetic(5, 2, "divide")   => returns 2.5
```
```
Try to do it without using if statements!
```

### My solution
```js
function arithmetic(a, b, operator){
  //your code here!
  switch(operator) {
    case 'add' :
      return a+b;
      break;
    case 'subtract' :
      return a-b;
      break;
    case 'multiply' :
      return a*b;
      break;
    case 'divide' : 
      return a/b;
      break;
  }
}
```
### Best practices

```js
function arithmetic(a, b, operator){
  //your code here!
  var mathFun = {
    'add': function (a, b) {
        return a+b;
    },
    'subtract': function (a, b) {
        return a-b;
    },
    'multiply': function (a, b) {
        return a*b;
    }, 
    'divide': function (a, b) {
        return a/b;
    }
  }

  return mathFun[operator](a,b);
}
```

### Comment
- 상대적으로 쉬운 문제였지만 시간이 없어서 요거로..ㅎ  
- 여러가지 베스트 풀이가 있지만 객체를 사용하는 방법을  
알아야겠다는 마음에서 저것을 가져왔다