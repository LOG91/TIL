## Multiplication Tables

Create a function that accepts dimensions, of Rows x Columns, as parameters in order to create a multiplication table sized according to the given dimensions. **The return value of the function must be an array, and the numbers must be Fixnums, NOT strings.  
  
  Example:

multiplication_table(3,3)

1 2 3
2 4 6
3 6 9

-->[[1,2,3],[2,4,6],[3,6,9]]

Each value on the table should be equal to the value of multiplying the number in its first row times the number in its first column.

### My Solution
```js
function multiplicationTable(row,col){
  //your code here
  let result = [];
  for(var i = 0; i < row; i++) {
    let arr = [];
    for(var j = 0; j < col; j++) {
      arr.push((j+1)*(i+1));
    }
    result.push(arr);
  }
  return result;
}
```

### Best Practices
```js
function multiplicationTable(row,col){
  out = []
  for (var i = 1; i <= row; i++)
  {
    temp = []
    // console.log(temp)
    for (var j = 1; j <= col; j++)
    {
      temp.push(i*j)
    }
    out.push(temp)
  }
  return out
}
```

### Comment
도무지 못풀거라 생각했는데 패턴을 보다보니 풀 수 있었다