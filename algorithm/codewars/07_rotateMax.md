## Rotate for max
```
Take a number: 56789. Rotate left, you get 67895.

Keep the first digit in place and rotate left the other digits: 68957.

Keep the first two digits in place and rotate the other ones: 68579.

Keep the first three digits and rotate left the rest: 68597. 

Now it is over since keeping the first four it remains only one digit which rotated is itself.

You have the following sequence of numbers:

56789 -> 67895 -> 68957 -> 68579 -> 68597

and you must return the greatest: 68957.

Calling this function max_rot (or maxRot or ... depending on the language)

max_rot(56789) should return 68957
```

### My solution
```js
function maxRot(n) {

  var result = n;
  n = n.toString().split('');
  
  for(var i = 0; i < n.length-1; i++){
    var moving = n[i];
    var be = parseInt(n.join(''));
    n.splice(i,1);
    n.push(moving);
    var af = parseInt(n.join(''));
    if(af > result) result = af;
  }
  
  return result;
}
```

### Best pretices
1. 
```js
function maxRot(n) {
    var str = n.toString();
    var arr = [str];
    for (var i=0;i<=str.length-1 ;i++){
        str = str.slice(0,i)+str.slice(i+1)+str[i];
        arr.push(str.split().join());
    }
    return Math.max.apply(null, arr);
}
```
2. 
```js
function maxRot(n){
  let max = n
  let arr = String(n).split('')
  for(let i = 0; i < arr.length; i++){
    arr.push(arr.splice(i,1))
    const num = Number(arr.join(''))
    if(num > max) max = num
  }
  return max
}
```

### Comment
무려 2시간이 걸렸다......  
알고리즘 = 절망 공식이 계속되서 적용되지만  
계속해서 싸워나가고 싶다
