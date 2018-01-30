## Categorize New Number

```
The Western Suburbs Croquet Club has two categories of membership, Senior and Open. 
They would like your help with an application form that will tell prospective members which category they will be placed.

To be a senior, a member must be at least 55 years old and have a handicap greater than 7. 
In this croquet club, handicaps range from -2 to +26; the better the player the lower the handicap.

Input
Input will consist of a list of lists containing two items each. 
Each list contains information for a single potential member. 
Information consists of an integer for the person's age and an integer for the person's handicap.

Note for F#: The input will be of (int list list) which is a List>

```
### Example Input

``` js
[[18, 20],[45, 2],[61, 12],[37, 6],[21, 21],[78, 9]]
```
### Output
``` 
Output will consist of a list of string values (in Haskell: Open or Senior) stating whether the respective member is to be placed in the senior or open category.
```
### Example Output
``` js
["Open", "Open", "Senior", "Open", "Open", "Senior"]
```

### My solution
```js
function openOrSenior(data){

  var ary = [];
  for(var i = 0; i < data.length; i++) {
    if(data[i][0] >= 55 && data[i][1] >7)ary.push('Senior');
    else ary.push('Open');
  }
  return ary;
}
```

### Best Practices
```js
function openOrSenior(data){
  function determineMembership(member){
    return (member[0] >= 55 && member[1] > 7) ? 'Senior' : 'Open';
  }
  return data.map(determineMembership);
}
```

### Comment
Iterator가 자스에서는 정말 많이 쓰인다고 한다  
공부하고 익숙해지도록 연습해야겠다