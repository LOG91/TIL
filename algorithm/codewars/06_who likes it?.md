## Who likes it?

You probably know the "like" system from Facebook and other pages. People can "like" blog posts, pictures or other items. We want to create the text that should be displayed next to such an item.

Implement a function likes :: [String] -> String, which must take in input array, containing the names of people who like an item. It must return the display text as shown in the examples:

```
likes [] // must be "no one likes this"
likes ["Peter"] // must be "Peter likes this"
likes ["Jacob", "Alex"] // must be "Jacob and Alex like this"
likes ["Max", "John", "Mark"] // must be "Max, John and Mark like this"
likes ["Alex", "Jacob", "Mark", "Max"] // must be "Alex, Jacob and 2 others like this"
```

### My solution
```js
function likes(names) {
  // TODO
  let sum = '';
  switch (names.length) {
    case 0 :
      sum = 'no one likes this';
      break;
    case 1 :
      sum = `${names[0]} likes this`;
      break;
    case 2 :
      sum = `${names[0]} and ${names[1]} like this`;
      break;
    case 3 :
      sum = `${names[0]}, ${names[1]} and ${names[2]} like this`;
      break;
    default :
      sum = `${names[0]}, ${names[1]} and ${names.length-2} others like this`;
      break;
  }
    return sum;
}
```

### Best practices
1. 
```js
function likes(names) {
  return {
    0: 'no one likes this',
    1: `${names[0]} likes this`, 
    2: `${names[0]} and ${names[1]} like this`, 
    3: `${names[0]}, ${names[1]} and ${names[2]} like this`, 
    4: `${names[0]}, ${names[1]} and ${names.length - 2} others like this`, 
  }[Math.min(4, names.length)]
}
```
2. 
```js
function likes (names) {
  var templates = [
    'no one likes this',
    '{name} likes this',
    '{name} and {name} like this',
    '{name}, {name} and {name} like this',
    '{name}, {name} and {n} others like this'
  ];
  var idx = Math.min(names.length, 4);
  
  return templates[idx].replace(/{name}|{n}/g, function (val) {
    return val === '{name}' ? names.shift() : names.length;
  });
}
```

### Comment
- 6단계 치고는 쉬운 문제였는데 이제 7단계는 안풀게 되어서 좋다!  
- 남의 코드를 보고 배우는 습관을 들여야겠다!