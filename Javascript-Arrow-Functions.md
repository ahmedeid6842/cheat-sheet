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