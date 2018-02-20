## Shortest Word
```
x Simple, given a string of words, return the length of the shortest word(s).

String will never be empty and you do not need to account for different data types.
```

### My solution
```js
function findShort(s){
s = s.split(' ');
let min = s[0];
  for(var i = 0; i < s.length; i++) {
    if(s[i].length < min.length) min = s[i];
    console.log(min.length);
  }
  return min.length;
}
```

### Best pratices
```js
function findShort(s){
  return Math.min.apply(null, s.split(' ').map(w => w.length));
}
```

### Comment
새 함수를 배우기에 아직 여유가 없는 것 같다.