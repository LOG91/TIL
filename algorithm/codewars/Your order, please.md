## Your order, please
Your task is to sort a given string. Each word in the String will contain a single number. This number is the position the word should have in the result.

Note: Numbers can be from 1 to 9. So 1 will be the first word (not 0).

If the input String is empty, return an empty String. The words in the input String will only contain valid consecutive numbers.

For an input: "is2 Thi1s T4est 3a" the function should return "Thi1s is2 3a T4est"

```js
your_order("is2 Thi1s T4est 3a")
[1] "Thi1s is2 3a T4est"
```

### My Solution
```js
function order(words){
  // ...
  var arr = words.split(' ');
  arr.sort(function(a, b){
  var nameA = a.split('').filter(function(v){if(Number(v))return v});
  var nameB = b.split('').filter(function(v){if(Number(v)) return v});
  if (nameA < nameB) {
    return -1;
  }
  if (nameA > nameB) {
    return 1;
  }
  });
  return arr.join(' ');
}
```

### Best Practies
```js
function order(words){
  
  return words.split(' ').sort(function(a, b){
      return a.match(/\d/) - b.match(/\d/);
   }).join(' ');
}  
```

### Comment
정규표현식을 배우고 싶은데 현재는 배울 여력이 안된다  
여유가 있을 때 조금씩이라도 공부해야겠다 .