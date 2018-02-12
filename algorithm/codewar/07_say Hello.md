## Say Hello!
```
Write a function to greet a person.
Function will take name as input and greet the person by saying hello. 
Return null/nil if input is empty string or null/nil.
```
Example : 
```js
greet("Niks") === "hello Niks!";
greet("") === null; // Return null if input is empty string
greet(null) === null; // Return null if input is null
```

### MY solution
```js
function greet(name) {
  return (name === "" || name === null) ? null : `hello ${name}!`;
}
```

### Best practices
```js
function greet(name) {
  return name ? 'hello ' + name + '!' : null;
}
```

### Needs

### Comment
^.^...