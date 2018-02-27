# If you can read this...
The idea for this Kata came from 9gag today.here

You'll have to translate a string to Pilot's alphabet (NATO phonetic alphabet) wiki.

Like this:

Input: If you can read

Output: India Foxtrot Yankee Oscar Uniform Charlie Alfa November Romeo Echo Alfa Delta

Some notes
- Keep the punctuation, and remove the spaces.
- Use Xray without dash or space.

Reference

alt text

You can use the NATO hash with the alphabet  
  
### My solution
```js
function to_nato(words) {

  var splited = words.split('');
  var upperFirstWord = splited.map(function(num, index,array){
    var nato = ch2nato(num);
    var lower = nato.toLowerCase();
    return lower.charAt(0).toUpperCase() + lower.slice(1);
  })
  var result = upperFirstWord.filter(function(x){return x !== ' '});
  return result.join(' ');
	// Go code
  function ch2nato(ch) {
    switch (ch.toLowerCase()) {
        case "a": return "ALFA";
        case "b": return "BRAVO";
        case "c": return "CHARLIE";
        case "d": return "DELTA";
        case "e": return "ECHO";
        case "f": return "FOXTROT";
        case "g": return "GOLF";
        case "h": return "HOTEL";
        case "i": return "INDIA";
        case "j": return "JULIETT";
        case "k": return "KILO";
        case "l": return "LIMA";
        case "m": return "MIKE";
        case "n": return "NOVEMBER";
        case "o": return "OSCAR";
        case "p": return "PAPA";
        case "q": return "QUEBEC";
        case "r": return "ROMEO";
        case "s": return "SIERRA";
        case "t": return "TANGO";
        case "u": return "UNIFORM";
        case "v": return "VICTOR";
        case "w": return "WHISKEY";
        case "x": return "XRAY";
        case "y": return "YANKEE";
        case "z": return "ZULU";
    }
    return ch;
}
}
```

### Best Pratices
```js
let table = {
  'A': 'Alfa',
  'B': 'Bravo',
  'C': 'Charlie',
  'D': 'Delta',
  'E': 'Echo',
  'F': 'Foxtrot',
  'G': 'Golf',
  'H': 'Hotel',
  'I': 'India',
  'J': 'Juliett',
  'K': 'Kilo',
  'L': 'Lima',
  'M': 'Mike',
  'N': 'November',
  'O': 'Oscar',
  'P': 'Papa',
  'Q': 'Quebec',
  'R': 'Romeo',
  'S': 'Sierra',
  'T': 'Tango',
  'U': 'Uniform',
  'V': 'Victor',
  'W': 'Whiskey',
  'X': 'Xray',
  'Y': 'Yankee',
  'Z': 'Zulu',
}

function to_nato(words) {
  return words.split('').filter(c => c !== ' ').map(c => table[c.toUpperCase()] || c).join(' ');
}
```

### Comment
1시간도 넘게 걸리긴 했지만 나의 첫 6레벨 성공이 굉장히 감격스럽다..  
switch문은 다행히도 직접 쓰진 않았고 구글에 nato를 검색하니 어떤 github에 있어서 퍼왔다  
```
function to_nato(words) {
  return words.replace(/\s/g, '').toLowerCase().split('').map(e => NATO[e] ? NATO[e] : e).join(' ');
}
```
베스트 풀이에 이런 것도 있었다!  
오래걸리기도 하고 실력이 잘 늘지는 않아도 이렇게 해서  
배워가는 것 같아서 좋다 ^^