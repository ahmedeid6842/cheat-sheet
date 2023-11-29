<h1 align="center"> JavaScript Execution Context </h1>

<div align="center">

<img src="https://miro.medium.com/v2/resize:fit:1073/0*xEkQsFkew0lqGqVJ.png" />

</div>

**Execution Context:** he environment in which the JavaScript code is executed. It consists of variables, functions, objects, and the scope chain that are available at a particular point during the execution of code.

### Execution Context

> #### 👀 a wrapper to help manage the code that is running  it contain things beyond what you’ve written in you code **like assigning global object and this**
>

<div align="center">

<img src="https://github.com/ahmedeid6842/ahmedeid6842/assets/57197702/1a70abbb-54f4-4817-a337-e896604bcd0c" alt="Execution context" />

</div>

### Execution Context Creation Phase

> #### 👀 this phase run through you identifies and function and  set up the prop memory space
>

<div align="center">

<img src="https://github.com/ahmedeid6842/ahmedeid6842/assets/57197702/fa576529-3e11-4122-a1bd-45659fa144f8" />

</div>

### Hoisting

**hoisting** : happen because in the execution context  “creation phase” the js engine try to set up the memory space for your variables and your function so when “code phase” come you `var`  variables and `function` are assigned to memory before 

```jsx
draw();
console.log(x);
var x =5 ; 
function draw(){
console.log("welcome again")
}
```

<div align="center">

<img src="https://github.com/ahmedeid6842/ahmedeid6842/assets/57197702/fa576529-3e11-4122-a1bd-45659fa144f8" />

</div>

### Undefined

> **🔥 `undefined`** : means that your variable have a space in memory but not defined or assigned to value yet
represents lack of existence
>

```jsx
console.log(x); // will print undefined ,,, hoi
var x = 5;
```

> 🔥 will print `undefined`  because of hoisting in create execution context phase assign `x` var to `undefined`  which means js reserve a space in memory but not assigned yet to value.
>

```jsx
console.log(x); // will print undefined ,,, hoi
var x = 5;
```

### Function Invoke & Execution Stack

> ##### 🔥 with every function invoke , a new execution context assigned to this function  when it’s end execution it will pop up out of execution stack
>

_function invoke means you call function to be executed_


<div align="center">

<img src="https://github.com/ahmedeid6842/ahmedeid6842/assets/57197702/760a850b-08de-4bb6-983f-3217c80ffe80" />

</div>

```jsx
function b(){
}
function a(){
	b();
}
a();
```

### Function Context And Environment Variables

> #### 🔥 with every function invoke it’s create own execution context execution context of a function include environment variables which you defined inside this function
>

> 👀 **in picture below** : `b()`will search first inside it’s own environment variables about `myVar` variables
>

<div align="center">

<img src="https://github.com/ahmedeid6842/ahmedeid6842/assets/57197702/9a0cb172-7b2c-4880-ba1b-5f8265b71e55" />

</div>

```jsx

function b(){
	var myVar;
	console.log(myVar); //will print undefined because b look at it's own execution context 
	// in case if b can't find myVar on it's own execution scope it will look at reference env variables
}

function a(){
	var myVar=2;
	b();
}

var myVar = 1;
a();

```

### Scope Chain

> 🔥 scope chain is about where I should search if I can’t find it inside my execution context or environment variables
>

> 👀 **in picture below** : `myVar` variables called in `b()` function , but it doesn’t defined inside it . 
so js engine search for it inside outer environment reference**
>

<div align="center">

<img src="https://github.com/ahmedeid6842/ahmedeid6842/assets/57197702/f6ee3d66-15f5-46bb-bc34-427dd438ca04" />

</div>


```jsx
function b(){
	console.log(myVar);
}

function a(){
	var myVar=2;
	b();
}

var myVar = 1;
a(); // it will print 1
```

> #### 🔥 reference outer environments determined based on where lexically putting this function in your code.     in other word : who created me not who called me
>

### Asynchronous

> #### 🔥 Async is about what happen outside the JS engine but JS engine working as Sync.
>

> 🔥 **in pictures below** : we have two methods click event and HTTP request so JS engine place them in Event Queue and execute them FIFO
>

<div align="center">

<img src="https://github.com/ahmedeid6842/ahmedeid6842/assets/57197702/80f25263-84ca-44cc-b870-3ab4e5e15f9b" />

</div>

> 👀 **in pictures below** : click event will be placed first in our execution stack and after it’s finished will place http request

<div align="center">

<img src="https://github.com/ahmedeid6842/ahmedeid6842/assets/57197702/efc8ac44-fa34-4910-93e8-d23f87a7e8b9" />

</div>

```jsx
function waitThreeSecond(){ // this function will take three second of execution
	var ms = 3000+ new Date().getTime();
	while(new Date() < ms){}
	console.log("finished function")
}

function clickHandler(){
	console.log('click event!')
}

document.addEventListener('click',clickHandler);
waitThreeSecond();
console.log('finished execution');
```


> #### 🔥 in example above : if we click it will be placed inside event queue until wait three second finished
>

### Coercion

> #### 👀 is about JS engine try to understand and find appropriate variables
#### 🔥 in code below we add number with string so JS coercion try to find suitable data type to complete the add operation
>

### Comparison Operator

```jsx
console.log(3<2<1); // this will print true 
/*
3<2 = > false
console.log(false<1);
console.log(true);
*/
```

> 🔥 in code above it print true because < operator goes from left to right,
so it will compare `3<2` and return the value of it which is `false`  then compare the rest of comparison `false<1` the result is true because false is equal 0 and 0 is less than 1
>

> 🔥 Number(undefined) : NAN
Number(null) : 0
Number(false) : 0
>