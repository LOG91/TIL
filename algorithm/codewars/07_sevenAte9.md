## SevenAte9

```
Write a function that removes every lone 9 that is inbetween 7s.
sevenAte9('79712312') => '7712312'
sevenAte9('79797') => '777'
```

### My solution

```js
function sevenAte9(str){
  let str = str.toString.split('');
  for (let i = 0; i < str.length; 1; i++) {
    if (strArray[i] === '7' && strArray[i + 1] === '9' && strArray[i + 2] === '7')
      strArray.splice(i , 1);
  }
  
  return strArray.join('');
}
```

### Best practices

```js
function sevenAte9(str){
  return str.replace(/79(?=7)/g, '7');
}
```

### Needs
Regualr Expression
### Comment
