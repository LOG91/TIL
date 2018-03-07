## Write Number in Expanded Form

You will be given a number and you will need to return it as a string in Expanded Form. For example:
```js
expandedForm(12); // Should return '10 + 2'
expandedForm(42); // Should return '40 + 2'
expandedForm(70304); // Should return '70000 + 300 + 4'
```
### My solution
```js
function expandedForm(num) {
  // Your code here
  var mapped = num.toString().split('').map(function(a, b, c) {
    if(a !== '0'){
    var result = parseInt(a) * Math.pow(10, (c.length - 1 - b));
    return result;
    }
  });
  return mapped.filter(function(a){return a !== undefined}).join(' + ');
}
```

### Best Practices
```js
const expandedForm = n => n.toString()
                            .split("")
                            .reverse()
                            .map( (a, i) => a * Math.pow(10, i))
                            .filter(a => a > 0)
                            .reverse()
                            .join(" + ");
```

### Comment
지금껏 코드워즈 하면서는 가장 뿌듯한 풀이이자 걸린 시간이었다  
그와 동시에 베스트 풀이를 보고 소름이 돋았다