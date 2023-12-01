<h1 align="center"> 🏹 Javascript Arrow Functions 🎯 </h1>

<div align="center">

<img src="https://usemynotes.com/wp-content/uploads/2021/05/what-is-an-arrow-function-in-javascript.jpg" alt= "javascript arrow functions">

</div>

### 📑 Table of Contents
- [What are Arrow Functions 🤔](#what-are-arrow-functions-🤔)
- [Usage of Arrow Functions 🧩](#usage-of-arrow-functions-🧩)
- [Differences between Arrow Functions and Named Functions 🔄](#differences-between-arrow-functions-and-named-functions-🔄)
- [Code Examples  💻](#code-examples-💻)
- [Summary 📃](#summary-📃)

## What are Arrow Functions? 🤔
Arrow functions, also known as fat arrow functions, are a concise way to write functions in JavaScript. They were introduced in ECMAScript 6 (ES6) and provide a more compact syntax compared to traditional named functions.

## Usage of Arrow Functions 🧩
1. **Shorter Syntax**: Arrow functions allow you to write functions with a shorter and more readable syntax.
2. **Lexical `this` Binding**: Arrow functions do not have their own `this` value. Instead, they inherit the `this` value from the surrounding context in which they are defined. This can be useful in avoiding the confusion of `this` binding in traditional functions.
3. **Implicit Return**: If the function body consists of a single expression, arrow functions automatically return the result of that expression without the need for an explicit `return` statement.

## Differences between Arrow Functions and Named Functions 🔄
1. **Syntax**: Arrow functions have a more concise syntax compared to named functions. They omit the `function` keyword and use a fat arrow (`=>`) instead.
2. **`this` Binding**: Arrow functions. Named functions, on the other hand, have their own `this` value, which is determined by how the function is called lexically.
3. **Arguments Object**: Arrow functions do not have their own `arguments` object. Instead, they inherit the `arguments` object from the surrounding scope. Named functions have their own `arguments` object, which contains the arguments passed to the function.
4. **Constructor Function**: Arrow functions cannot be used as constructor functions to create new objects. Named functions can be used as constructor functions with the `new` keyword to create new instances of objects.

## Code Examples  💻

### Named Function
```javascript
function greet(name) {
  return "Hello, " + name + "!";
}
```

### Arrow Function
```javascript
const greet = (name) => {
  return "Hello, " + name + "!";
};
```

### Arrow Function with Implicit Return
```javascript
const greet = (name) => "Hello, " + name + "!";
```

### `this` Binding in Arrow Functions
```javascript
const person = {
  name: "John",
  greet: function() {
    setTimeout(() => {
      console.log("Hello, " + this.name + "!");
    }, 1000);
  }
};

person.greet(); // Output: Hello, John!
```

### `this` Binding in Arrow vs Named Functions in a Class
In the context of a class, the `this` keyword in an arrow function refers to the instance of the class. In a named function, the `this` keyword refers to the global object (or `undefined` in strict mode) if the function is not called as a method of an object.

```javascript
class Test {
    constructor() {
        this.name = "Ahmed Eid";
        this.age = 24;
        this.job_title = "backend developer"
    }

    start() {
        setInterval(() => {
            console.log("start", this); // `this` refers to the instance of the Test class
        }, 5000)
    }

    end(){
        setInterval(function(){
            console.log("end",this); // `this` refers to the global object
        },6000)
    }

}
```

## Summary 📃

| Comparison                                 | Arrow Functions                                      | Named Functions                                      |
|--------------------------------------------|------------------------------------------------------|------------------------------------------------------|
| Syntax                                     | Concise syntax using `=>`                            | Traditional syntax using `function` keyword           |
| `this` Binding                             | Inherits `this` from surrounding code                | Has its own `this` value determined lexically         |
| `arguments` Object                         | Inherits `arguments` from surrounding scope           | Has its own `arguments` object                       |
| Constructor Function                       | Cannot be used as constructor functions              | Can be used as constructor functions with `new`       |