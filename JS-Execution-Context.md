# JavaScript Execution Context 

# section 1 : execution context and lexical analysis

> **execution context** : the environment in which your code is running is “Execution context”,
it’s create when you code executed
> 

## execution context

> #### 👀 a wrapper to help manage the code that is running  it contain things beyond what you’ve written in you code **like assigning global object and this**
>

![Untitled](https://github.com/ahmedeid6842/ahmedeid6842/assets/57197702/1a70abbb-54f4-4817-a337-e896604bcd0c)

## execution context creation phase

> #### 👀 this phase run through you identifies and function and  set up the prop memory space
>

![Untitled](https://github.com/ahmedeid6842/ahmedeid6842/assets/57197702/fa576529-3e11-4122-a1bd-45659fa144f8)

## hoisting

hoisting : happen because in the execution context  “creation phase” the js engine try to set up the memory space for your variables and your function so when “code phase” come you `var`  variables and `function` are assigned to memory before 

```jsx
draw();
console.log(x);
var x =5 ; 
function draw(){
console.log("welcome again")
}
```

![Untitled](https://github.com/ahmedeid6842/ahmedeid6842/assets/57197702/fa576529-3e11-4122-a1bd-45659fa144f8)

## undefined

> **🔥 `undefined`** : means that your variable have a space in memory but not defined or assigned to value yet
represents lack of existence
>

```jsx
console.log(x); // will print undefined ,,, hoi
var x = 5;
```

> 🔥 will print `undefined`  because of hoisting in create execution context phase assign `x` var to `undefined`  which means js reserve a space in memory but not assigned yet to value >
>

```jsx
console.log(x); // will print undefined ,,, hoi
var x = 5;
```