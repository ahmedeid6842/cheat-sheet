<a name="readme-top"></a>

<h1 align="center"> NodeJS the Guide to Build A RESTful APIs  </h1>
<img src="https://wallpaperbat.com/img/818879-node-js-wallpaper-top-free-node-js-background.png" />

# section 1 : Node Module System

#### 🔥 In Node.js every file considered as module, so functions and variables assigned to that module and can’t be accessed otherwise you allow that


```jsx
console.log(module); // will print module object for this file 
```


#### 👀 **exports :** is object that  part of module object, so anything inside the exports object will be global

```jsx
function log(){
console.log("hello");
}

module.exports.logging = log ; // assigned log function to logging object 
```

```jsx
const log = require("./log"); // load module.exports from ./log file 
log.log(); //call function 
```


## Events

```jsx
const EventEmitter = require("events");
const emitter = new EventEmitter();

//receive event : what happend when "log" event raised
emitter.on("log",(args)=>{
console.log(`welcome back ${args.name}`);
})

// Raise event
emitter.emit("log",{name : "ahmed"})
```

#### 🔥 order of code is important with events 
    1- define receiver of events
    2- raise event


#### 👀 to raise event in file and receive it in another file

- **log.js**

    ```jsx
        const EventEmitter = require("events");
        class Log extends EventEmitter {
            logging(){
                this.emit("hi",{name : "ahmed"})
            }
        }

        module.exports = Log;
    ```

- **index.js**

    ```jsx
        const Log = require("./log");
        const obj = new Log();

        obj.on("hi",(args)=>{
            console.log(`welcome ${args.name}`);
        })

        obj.logging();
    ```


## HTTP

#### 🔥 HTTP : is JS module that help us to create a server. http module is based on event module.

```jsx
const http = require("http");
const server = http.createServer(); 

server.on("connection",()=>{ // when a new connection established
		console.log("connected")
})
server.listen(3000); // listen to any event or request on port 3000
```

#### 👀 instead of using `on` method the `createServer()` can handle. your request and response

```jsx
const http = require("http");
const server = http.createServer((req,res)=>{
	if(req.url === "/"){
		res.write(`<h1>welcome again<h1>`);
	}
});

server.listen(3000);
```

# section 2 : Building REST APIs

>   🔥 REST : REpresentation State Transfer

>   👀 we have four main REST method: post , get , put , delete

>   👀 express : is package that use to build REST API based on http 

```jsx
const express = require("express"); // express package return function 
const app = express() ; // we need to call express function which return express object

app.get("/",(req,res)=>{
	res.send(req.url);
});

app.listen(3000,console.log("connected on port 3000")); // specify the port which listen to and where application are run 
```

#### 👀 in deployment port number are assigned automatically by the host using environment variable called `PORT` . to use environment variable we use `process.env.PORT`

```jsx
const express = require("express"); // express package return function 
const app = express() ; // we need to call express function which return express object

const port = process.env.PORT || 3000 ; 
app.listen(port,console.log("connected on port 3000")); // specify the port which listen to and where application are run 
```

## Route Parameter & Query

- ### route parameter

    > if you want to set parameter that passed with endpoint `localhost:3000/api/course/1`
    > 

    ```jsx
    app.get("/api/course/:id",(req,res)=>{
                res.send(req.params);
    })
    ```

- ### route query

    > if you want to set query which is optional with any endpoint
    `localhost:3000/api/course/1?name=ahmed`
    > 

    ```jsx
    app.get("/api/course/:id",(req,res)=>{
                res.send(req.query); // return {name : "ahmed"}
    })
    ```

> ##### 🔥 `app.use(express.json());` : express.json() calling middleware function. app.use() use this middleware in request processing 

## Validating object JOI

> Joi: npm package that easily validate data object
> 

```jsx
const Joi = require("joi");
const schema = Joi.object({ // create joi schema object 
	name: Joi.string().min(3).required()
})

schema.validate(req.body); //validate req.body object using your schema 
```

## PUT request

> example : update course by it’s id ⬇️
> 

```jsx
app.put("/api/courses/:id", (req, res) => {
    //look up the course
    const course = courses.find((element) => element.id === parseInt(req.params.id));
    //if not existing return 404
    if (!course) return res.status(404).send("no course found")

    //validate
    const { error } = validateCourse(req.body);
    //if invalid, return 400 - bad request 
    if (error) return res.status(400).send(error);

    //update course
    course.name = req.body.name;
    //return the updated  courses
    return res.send(course);
})
```

> ##### 🔥 when you send response `res.send()` use `return` keyword to stop the rest execution function
