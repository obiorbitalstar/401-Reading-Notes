# React 


## Variable declaration
ES6 introduced the let keyword, which allows for block-scoped variables which cannot be hoisted or redeclared.

```
let x = 0

```

## Constant declaration
ES6 introduced the const keyword, which cannot be redeclared or reassigned, but is not immutable.

```
const CONST_IDENTIFIER = 0 
```
## Arrow functions
The arrow function expression syntax is a shorter way of creating a function expression. Arrow functions do not have their own this, do not have prototypes, cannot be used for constructors, and should not be used as object methods

```
let func = (a) => {} // parentheses optional with one parameter
let func = (a, b, c) => {} // parentheses required with multiple 

```

## Implicit returns
The return keyword is implied and can be omitted if

 using arrow functions without a block body.

 ```
 let func = (a, b, c) => a + b + c // curly brackets must be omitted


```

## Key/property shorthand
ES6 introduces a shorter notation for assigning properties to variables of the same name.

```
var obj = {
  a: a,
  b: b,
}

```

## Method definition shorthand

```
let obj = {
  a(c, d) {},
  b(e, f) {},
}
```

# Hello World

```
ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('root')
);

```
