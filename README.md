# Understanding Scope and Hoisting in JavaScript

## Introduction

JavaScript is a versatile and powerful programming language widely used in web development. Two fundamental concepts every JavaScript developer must understand are **Scope** and **Hoisting**. This lecture will explain these concepts in detail, providing examples to illustrate their behavior.

## Scope

**Scope** in JavaScript refers to the current context of code execution, which determines the accessibility of variables and functions. There are two main types of scope:

1. **Global Scope**
2. **Local Scope**

### Global Scope

Variables declared outside any function or block are in the global scope. They can be accessed from anywhere in the code.

```javascript
let globalVar = "I am a global variable";

function accessGlobal() {
  console.log(globalVar); // Output: I am a global variable
}

accessGlobal();
console.log(globalVar); // Output: I am a global variable
```

### Local Scope

Variables declared within a function or block are in the local scope. They can only be accessed within that function or block.

#### Function Scope

Variables declared inside a function are function-scoped.

```javascript
function localFunction() {
  let localVar = "I am a local variable";
  console.log(localVar); // Output: I am a local variable
}

localFunction();
console.log(localVar); // Error: localVar is not defined
```

#### Block Scope

Variables declared with `let` or `const` inside a block (e.g., a loop or conditional statement) are block-scoped.

```javascript
if (true) {
  let blockVar = "I am a block-scoped variable";
  console.log(blockVar); // Output: I am a block-scoped variable
}

console.log(blockVar); // Error: blockVar is not defined
```

### Lexical Scope

JavaScript uses lexical scoping (also known as static scoping). This means that the scope of a variable is determined by its location within the source code, and nested functions have access to variables declared in their outer scope.

```javascript
function outerFunction() {
  let outerVar = "I am outside!";

  function innerFunction() {
    console.log(outerVar); // Output: I am outside!
  }

  innerFunction();
}

outerFunction();
```

## Hoisting

**Hoisting** is JavaScript's default behavior of moving declarations to the top of the current scope (script, function, or block). This behavior allows variables and function declarations to be used before they are declared.

### Variable Hoisting

With `var`, variable declarations are hoisted to the top of their scope and initialized with `undefined`.

```javascript
console.log(hoistedVar); // Output: undefined
var hoistedVar = "I am hoisted!";
console.log(hoistedVar); // Output: I am hoisted!
```

However, variables declared with `let` and `const` are hoisted but not initialized. Accessing them before the declaration results in a `ReferenceError`.

```javascript
console.log(hoistedLet); // Error: Cannot access 'hoistedLet' before initialization
let hoistedLet = "I am not hoisted!";
```

### Function Hoisting

Function declarations are hoisted to the top of their scope and can be called before they are declared.

```javascript
hoistedFunction(); // Output: I am a hoisted function!

function hoistedFunction() {
  console.log("I am a hoisted function!");
}
```

Function expressions, however, are not hoisted.

```javascript
hoistedExpression(); // Error: hoistedExpression is not a function

var hoistedExpression = function () {
  console.log("I am not hoisted!");
};
```

## Conclusion

Understanding scope and hoisting is crucial for writing efficient and bug-free JavaScript code. Remember:
- Scope determines the accessibility of variables and functions.
- Hoisting moves declarations to the top of their scope, but `let` and `const` variables are not initialized until their declaration is evaluated.

By mastering these concepts, you can avoid common pitfalls and write more predictable JavaScript code. Happy coding!
