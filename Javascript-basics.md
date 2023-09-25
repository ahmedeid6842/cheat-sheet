 <a name="readme-top"></a>

<h1 align="center"> JavaScript Basics for Beginners </h1>
<img src="https://github.com/ahmedeid6842/cheat-sheet/assets/57197702/bd580e39-bae5-4d17-b9a2-e14a01cd5347" />

- [Basics](#section-1--basics)
    - [Variable types](#there-are-two-types-of-variables--primitive-and-reference-data-type)
    - [Dynamic language](#javascript--is-dynamic-programming-language-exg)
    - [Objects](#object)
    - [Array](#array)
    - [Functions](#functions)
- [Operators](#section-2--operator)
    - [Equality operator](#equality-operator)
    - [Ternary operator](#ternary-operator-truefalse)
- [Control flow](#section-3--control-flow)
    - [if condition](#if-condition)
    - [switch case](#switch-case)
    - [for](#for)
    - [while](#while)
    - [do-while](#do-while)
    - [for-in](#for-in)
    - [for-of](#for-of)
    - [Exercises](#exercise--landscape-portrait)
- [Objects](#section-4--objects)
    - [defining an object](#defining-an-object)
    - [factory function](#factory-function)
    - [constructor function](#constructor-function)
    - [primitive and reference](#primitive-and-reference)
    - [Exercises](#exercise--address-object)
- [Arrays](#section-5--array)
    - [adding in array](#adding-in-array)
    - [removing in array](#removing-in-array)
    - [find in array](#find-in-array)
    - [emptying array](#emptying-array)
    - [combining array](#combining-array)
    - [spread operator](#spread-operator)
    - [iteration](#iteration)
    - [joining array](#joining-array)
    - [sorting array](#sorting-array)
    - [testing array](#testing-array)
    - [Exercises](#exercise--array-range)
- [Functions](#section-6--functions)
    - [arguments & parameters](#arguments--parameters)
    - [getter & setter](#getter-and-setter)
    - [errors & exception](#errors-and-exception)
    - [let vs var](#let-vs-var)
    - [This keyword](#this-keyword)
    - [Exercises](#exercise--area-of-circle)

---

# section 1 : Basics

## there are two types of variables : primitive and reference Data type

**primitive types**  
   String 
 Number
 Boolean
undefined 
      null

**reference types
       object
       array 
    function**

## javascript :  is dynamic programming language (ex)

```jsx
let check = "verified";
if(true){
	check = true ; // note : check variable above was string but here it's changed into true  
}
```

## Object

### defining object

```jsx
let obj = {
 key : "value",
 key2 : "value2"
} 
```

### accessing object

dot notation : console. log(objName.key);

bracket notation : console.log(objName[’key’]);

## Array

- array can store multiple data type let arr = [”ahmed”, “mohamed”,3];
- arrays the original of it, is object console.log(typeof(arr));

## Functions

### defining function

```jsx
function fun_Name(parameters){
	code 
	return value ;
}
fun_Name(argument); //calling function
```

# section 2 : Operator

## equality operator

- strict equality “===” : (type + value) the two values must be the same in the type an value
- lose equality “==” : the value must be equal in value only doesn’t matter the type ,,,, means “1” equal 1

## ternary operator ?true:false

```jsx
let point = 90 ;
let type = point > 100 ? 'gold' : 'sliver' ;
console.log(type);
```

# section 3 : Control flow

## if condition

```jsx
/*
if (condition){
	execute this statement
}else if (condition){
	execute this statement 
}else{
	execute this statement 
}
*/
let hour = 24;

if (hour >= 6 && hour <= 12) {
    console.log("good morning");
}else if (hour > 12 && hour < 18) {
    console.log("good afternoon")
} else {
    console.log("good evening");
}
```

## switch… case

```jsx
/*
let varName
switch(varName){
	case 1 : 
			execute this code
			break ;
	case 2 : 
			execute this code 
			break ;
	default : 
			execute this code 
			break;
}
*/
let hour = 2;
switch (hour) {
    case 1:
        console.log("good morning");
        break;
    case 2:
        console.log("good evening");
        break;
    default:
        console.log("default");
        break;
}
```



## for

it’s used to repeat block of code number of times 

```jsx
/*
for(intial expression ; condtion ; iteratble ){
	code block
}
*/
for(let i =0 ; i<5;i++){
		console.log(hello world);
}
```

## while

while loop to iterate based on condition ,,, initial expression doesn’t set in it’s body 

```jsx
/*
while(condition){
code
}
*/
let i=0; 
while(i>5){
console.log(i);
i++
}
```

## do-while

it execute your code then check your condition ,,, it’s guarantee execute your code at least once 

```jsx
/*
do{

}while(condition)
*/
do {
    console.log("hi")
}while(false)
```

## for-in

it iterate over your object keys ,,, don’t have to use tradition defination of for(intial express; cond; ++)

```jsx
for(let key in object){
 console.log (key , object[key])
}
///////////////////////////////
for(let key in arr){
	console.log(key,arr[key]); // in this example the key will be indeces of your array
}
```

## for-of

it iterate over your array value ,

<aside>
👀 note : you can’t use for-of with object because it’s not iteratble data type

</aside>

```jsx
for(let value of arr){
	console.log(value)
}
```

## exercise : Landscape portrait

```jsx
function isLandScape(width,height) {
    return (width>height)
}
console.log(isLandScape(100, 96));
```

## exercise : fizzbuzz

```jsx
// divisble by 3 => fizz
// divisble by 5 => Buzz
// divisble by both 3 and 5 => fizzBuzz
// not divisble by both 3 or 5 => input
// not a number => "not a number"

function fizzBuzz(input) {
    if (typeof input != "number") {
        console.log("not a number");
        return;
    }
    if (input % 3 == 0 && input % 5 == 0) {
        console.log("fizzBuzz");
    } else if (input % 5 == 0) {
        console.log("Buzz");
    } else if (input % 3 == 0) {
        console.log("fizz");
    } else {
        console.log(input);
    }
}

fizzBuzz(3);
fizzBuzz(5);
fizzBuzz(15);
fizzBuzz(7);
fizzBuzz("hi");
```

## exercise : demerit points

```jsx
//speed limit = 70
// 5 => 1 point 
// Math.floor(1.3)
// 12 points -> suspended 

function checkSpeed(speed) {
    points = Math.floor((speed - 70) / 5);
    if (points == 0) {
        console.log("you are OK");
    } else if (points > 12) {
        console.log("suspended");
    } else {
        console.log(points);
    }
   
}

checkSpeed(180);
```

## exercise : even or odd

```jsx
// number = 10
// 0 -> 10 determine if even or odd 

function showNumbers(limits) {
    let type;
    for (let i = 0; i <= limits; i++) {
        type = i % 2 == 0 ? "even" : "false";
        console.log(i, type)
    }
}

showNumbers(10);
```

## exercise : string properties

```jsx
// print string values in an object

let person = {
    name: "ahmed",
    age: 25,
    grade: "A"
}

showProperties(person);

function showProperties(obj) {
    for (let key in obj) {
        if (typeof obj[key] == "string") {
            console.log(key, obj[key]);
        }
    }
}
```

## exercise : sum of multiple

```jsx
// print string values in an object

let person = {
    name: "ahmed",
    age: 25,
    grade: "A"
}

showProperties(person);

function showProperties(obj) {
    for (let key in obj) {
        if (typeof obj[key] == "string") {
            console.log(key, obj[key]);
        }
    }
}
```

## exercise : Grade

```jsx
// average
// 1-59 : F
// 60-69 : D
// 70-79 : C
// 80-89 : B
// 90-100 : A 

const marks = [80, 80, 50];

function calculateGrade(marks) {
    let sumGrade = 0 , average;
    for (let value of marks) {
        sumGrade += value;
    }
    average = sumGrade / marks.length;
    if (average > 90 && average <= 100)
        return "A"; 
    if (average > 80 && average <= 90)
        return "B"
    if (average > 70 && average <= 80)
        return "C"
    if (average > 60 && average <= 70)
        return "D"
    if (average > 1 && average <= 59)
        return "F"
    
}

console.log(calculateGrade(marks));
```

## exercise : show stars

```jsx
// print stars
// showstars(5)
//*
//**
//***
//****
//*****
function showStars(number) {
    for (let i = 0; i <= number; i++) {
        let output = "";
        for (let j = 0; j < i; j++) {
            output += "*"
        }
        console.log(output);
    }
}

showStars(5)
```

## exercise : show primes

```jsx
// showPrimes(10)
// show prime number between 1 to  10

function showPrimes(limit) {
    for (let number = 2; number < limit; number++){
        let status = true ;
        for (let factor = 2; factor < number; factor++){
            if (number % factor == 0) {
                status = false;
                break;
            }
        }
        if (status == true) console.log(number);
    }
}
showPrimes(2);
```

# section 4 : Objects

> **Object** : it’s used to hold multiple property with different data types related to one big variable
              like circle “object” with it’s  property “radius , color”
> 

## defining an object

```jsx
let  circle = {
      radius : 5,
			color: "string",
			draw(){ //method
				console.log(radius,color)
			}
};

circle.draw();
console.log(circle.radius)
```

<aside>
👀 if function part of object we call it **method** like “draw function above”

</aside>

## factory function

**factory function :** is used to define multiple object 
for example if we have multiple circle we don’t have to implement new object for each one 
**camal notation** 

```jsx
function factoryFunction(radius, color) {
    return {
        radius,
        color,
        draw() {
            console.log(`radius:${radius} color:${color}`);
        }
    }
}
let circle1 = factoryFunction(1, "blue");
let circle1 = factoryFunction(2, "green");
circle1.draw();
circle2.draw();
```

## constructor function

**constructor function :** it’s the same as factory function with different implementation 
**pascal notation**

```jsx
function ConstructorFunction(radius, color) {
    this.radius = radius; 
    this.color = color;
    this.draw = function (radius, color) {
        console.log(`radius:${this.radius} color:${this.color}`);
    }
}

let circle1 = new ConstructorFunction(2, "green");
circle1.draw();
```

new key word do three things : 

1. create new empty object 
2. assign this.property to the new object 
3. return the object with it’s property 

## Primitive and reference

**primitives data types** : are copied by value                                                     “string,number,bool,..etc”  

```jsx
let x=5 ;
let y=x; // we copy value of x into y
x++;
console.log(y); // will print 5 
```

**references data types** : are copied by reference                                               “object , array , function ”  


```jsx
let x = {value : 20 }
let y = x ;
x.value++ ;
console.log(y.value); // will print 21 because we change the refernce of value object in memory
```

### cloning object

we have three different way to copy values of object into another object : 

1. iterate over each value in the object and copy it to another value

```jsx
let person= {
	name:"ahmed",
	age: 30
}

let person2 = {}
for(let key in Object.keys(person)){
	person2[key] = person[key]
}
```

1. using spread operator … 

```jsx
let person= {
	name:"ahmed",
	age: 30
}

let person2= {...person};
```

1. using Object.assign() method

```jsx
let person= {
	name:"ahmed",
	age: 30
}

let perons2 = Object.assign({},person); // {} is intial object that added person to it
```

## exercise : address object

```jsx
function showAdress(adress) {
    for (let key in adress)
        console.log(`${key} : ${adress[key]}`);
}

let adress = {
    street: "bank street",
    city: "ismalia",
    zipcode: 562,

}

showAdress(adress);
```

## exercise : constructor & factory address object

```jsx
function ConstructorFunction(street, city, zipcode) {
    this.street = street; 
    this.city = city; 
    this.zipcode = zipcode;
}

function factoryFunction(street, city, zipcode) {
    return {
        street,
        city,
        zipcode,
    }
}

let address1 = new ConstructorFunction("bank street", "ismalia", 456);
let address2 = factoryFunction("bank street", "ismalia", 456);

console.log(address1);
console.log(address2);
```

## exercise : Object equality

```jsx
// areEqual(obj1, obj2) => check if the two object are equal in values and keys
// areSame(obj1,obj2) => check if the two object points to the same adress

function ConstructorFunction(street, city, zipcode) {
    this.street = street; 
    this.city = city; 
    this.zipcode = zipcode;
}

let address1 = new ConstructorFunction("bank street", "ismalia", 456);
let address2 = new ConstructorFunction("bank street", "ismalia", 456);
let address3 = address1

function areEqual(address1, address2) { 
    for (let key in address1) {
        if (address1[key] !== address2[key])
            return false;
    }
    return true; 
}

function areSame(address1, address2) {
    return address1 === address2 ? true : false; 
}
console.log(areEqual(address1, address2));
console.log(areSame(address1, address3));
```

# section 5 : array

## adding in array

we have three ways  with three different position for add into array : 

1. at the end: arr.push(5);
2. at the front : arr.unshift(1);
3. at the middle : arr.splice(1,0,5);

```jsx
let arr = [1,2,3];
arr.push(4); //adding at the end
arr.unshift(1); //adding at the front
arr.splice(1,0,5,6,7); //adding at the middle ,,, splice(index elemetnt to start with , Nof element in you want to delete , elements you want to add)
```

## removing in array

we have three ways  with three different position for deleting from array : 

1. at the end: arr.pop(5);
2. at the front : arr.shift(1);
3. at the middle : arr.splice(1,2);

```jsx
let arr = [1,2,3];
arr.pop(4); //removing at the end
arr.shift(1); //removing at the front
arr.splice(1,2); //adding at the middle ,,, splice(index elemetnt to start with , Nof element in you want to delete , elements you want to add)
```

## find in array

- to find index of element in array we use **arrName.findIndex(element)**
- to check if the element exists in array or not we use **arrName.includes(element)**
- to find reference datatype element we  use arrName.find((element) ⇒ return condition)
- to find index of  reference datatype element we  use arrName.findIndex((element) ⇒ return condition)

```jsx
let arr = [3,4,5,6];
console.log(arr.findIndex(3)); // will print 0
console.log(arr.includes(7)); // will return false because "arr" doesn't have "7"

let persons = [
    { name: "ahmed eid", age: "24" },
    { name: "soliman faisel", age : "42"}
]

console.log(persons.find((element) => {
    return element.name == "ahmed eid"
}))
console.log(persons.findIndex((element) => {
    return element.name == "soliman faisel"
}))
```

## emptying array

- arr = [] we use this way if your array doesn’t refered by other variables
- arr.length=0
- arr.splice(0,arr.length);

## combining  array

- concat method : used to merge two arrays and return array as result
- slice : to cut a slice or part of an array and return it

```jsx
let arr1=[1,2,3];
let arr2=[4,5,6];
let result = arr1.concat(arr2); // result = [1,2,3]+[4,5,6] = [1,2,3,4,5,6]
let shot = arr.slice(2,4);
```

<aside>
🔥 those two method when we use in array of reference data type like object it’s concat by refernce

</aside>

<aside>
🔥 we can use slice to take a copy of arrays value into another array  ,,, copy by value
let arr1=[1,2,3]
let arr2= arr1.slice()

</aside>

## spread operator

- take a copy or merge arrays to new array

```jsx
let arr=[1,2,3];
let arr2=[4,5,6];
let result = [...arr1,"a","b","c", ...arr2]
```

## iteration

```jsx
let arr = ["first","second","third"] ; 
arr.forEach((element)=>{console.log(`this is ${element}`)}) ; // this iteration don't change the orginal value of array
```

## joining array

we have two methods : 

- join() : convert array to string            [1,2,3].join(”/”) ⇒ “1/2/3”
- split(): convert string to array            “hello it’s me”.split(” “) ⇒ [”hello”, ”it’s” , “me” ]

## sorting array

we have two methods : 

- sort() : sort array from assending                  [1,7,2,5,3].sort() ⇒ [1,2,3,5,7]
- reverse() : reverse the array elements            [1,2,3,5,7].reverse() ⇒ [7,5,3,2,1]

## testing array

we have two methods : 

- every () : to check that every element in array based in condition
- some() : to check if at least one of the element do condition

```jsx
let arr1 = [2,4,6,8] ; 
let arr2 = [-1,4,2,3];

let checkEven = arr1.every(element => element%2==0);
let atLeastOneNegative = arr.some(element => element<0)
```

## filter array

return filtered array based on condition

```jsx
let arr = [-1,4,2,3];
let onlyPositive = arr.filter(element => element>0)
```

## exercise : array range

```jsx
function arrRange(start, end) {
    let arr = [];
    for (start; start <= end; start++)
        arr.push(start);
    return arr;
}

let result = arrRange(1, 5);
console.log(result);
```

## exercise : includes

```jsx
function includes(arr, searchElement) {
    for (let value of arr) {
        if (searchElement === value)
            return true;
    }
    return false;
}

let arr = [1, 2, 3, 4];
console.log(arr.includes(2));
```

## exercise : except

```jsx
// remove elements from array
function except(array, execluded) {
    return array.filter((elemment) => {
        return !(execluded.includes(elemment))
    })
    
}
let numbers = [1, 2, 3, 4];
const output = except(numbers, [1]);
console.log(output);
```

# section 6 : functions

## arguments & parameters

> every function have a special object called arguments
 which return parameters you passed as itertable object  object
it’s useful if you have undetermined number of arguments
> 

```jsx
function person(){
	console.log(arguments);
}

person("ahmed",24,"egypt");
```

> if you want to point to group of arguments in one parameter we use spread operator “…”
it return parameters as an array
> 

```jsx
function person(name,...parameters){
		console.log(name); // this will print "ahmed"
		console.log(parameters); // this will print [25, "egypt","software"]
}
person("ahmed",25,"egypt","software");
```

### default paramters

```jsx
function person(name,age = 22 , address){
	console.log(name,age,address); // this will print "ahmed",22,address
}
person("ahmed",undefined, "egypt");
```

## getter and setter

> getter and setter : if we want to create a function that return object data and access it as property with dot notation
> 

```jsx
let person = {
    firstName: "ahmed",
    lastName: "eid",
    get fullName() {
        return `${this.firstName} ${this.lastName}`
    },
    set fullName(value) { 
        fullNameArray = value.split(" ")
        this.firstName = fullNameArray[0];
        this.lastName = fullNameArray[1];
    }
}

person.fullName = "mohamed hassan"
console.log(person.fullName);
```

## errors and exception

<aside>
🔥 error is defining Error object, exception where we throw the error we define

</aside>

```jsx
function onlyPositive(number) {
    if (number < 0) {
        throw new Error("only positive values");
    } else {
        console.log(`${number} is postive`);
    }
}

try {
    onlyPositive(-5)
} catch (error) { // error : is the Error object we throw
    console.log(error);
}
```

## let vs var

<aside>
🔥 let is block scope but var is function scope

</aside>

```jsx
//let 
function test(){
		if(true){
		let number = 5;
		}
		console.log(number); // will return error because "number" variable aren't defined in this scope
}

//var 
function test2(){
	if(true){
	var number = 5;
	}
	console.log(number); // will return "5" because "number variables" assigned to test2() function scope
}
```

<aside>
🔥 var isn’t recommended because if we define it in global scope it’s assigned to window object
so if window object use third party that have the same var variable name it will be overwritten

</aside>

## This keyword

<aside>
🔥 this is the object that executing the current object

</aside>

```jsx
let obj = {
	name:"ahmed",
	tags : ["egypt",25,"bank street"]
	display(){
		console.log(this)
	}
}

obj.display(); // it's will print the object that contain this obj = {name: "ahmed , tags : [...]} 
```

> in methods this refer to object which it’s belongs to
in functions this refer to window or global object
> 

```jsx
let obj = {
	name:"ahmed",
	tags : ["egypt",25,"bank street"]
	display(){
		console.log(this) // this refers to obj object 
	}
}
function test(){
	console.log(this); //this refer to window object
}
```

### changing this

```jsx
let obj = {
	name:"ahmed",
	tags : ["egypt",25,"bank street"]
	display(){
		this.tags.forEach(function (tag){
			console.log(this.name); // it will print undefined because "this" refer to window object
			// function is part of window scope 
		})
	}
}

//solution1 bind()
// bind() it's bind your function to new object and return new function with new object binded  
let obj = {
	name:"ahmed",
	tags : ["egypt",25,"bank street"]
	display(){
		this.tags.forEach(function (tag){
			console.log(this.name); 
		}.bind(this));
	}
}

//solution2 arrow function
// arrow function ()=>{} : inhernet this from containg function 
let obj = {
	name:"ahmed",
	tags : ["egypt",25,"bank street"]
	display(){
		this.tags.forEach((tag)=>{
			console.log(this.name); 
		});
	}
}
```

## exercise : sum of arguments

```jsx
// return sum of arguments you passed in calling
// although accept if the arguments is array 

function sum(...pars) {
    let total = 0;

    for (let value of pars) {
        if (Array.isArray(value)) {
            for (let arrValue of value) {
                total += arrValue;
            }
        } else {
            total += value;
        }
    }
    return total;
}
console.log(sum([1,2,3,4,5],1, 2, 3, 4, [6],5));
```

## exercise : area of circle

```jsx
let circle = {
    radius: 5,
    get area() {
        return Math.PI * Math.pow(this.radius, 2);
    },
    set radiusSet(value) {
        this.radius = value;
    }
}

circle.radiusSet = 10;
console.log(circle.area);
```