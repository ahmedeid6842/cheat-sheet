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


# section 3 : Express advanced topics

## Middleware

> #### 👀  middleware is function that take request object and either return response to the client or passes control to another middleware function in request processing pipeline
> 

![Untitled](https://github.com/ahmedeid6842/cheat-sheet/assets/57197702/7f8db80e-e94a-4e99-8d7f-d78255b71e3e)

```jsx
app.use(function (req,res,next){
		next(); // next passes the control to next middleware function 
})
```

> `express.static()` : is middleware that serve static page 
`express.urlencoded()` : is middleware that convert form template to object 
`morgan(”tiny”)` : middleware that log requests in console
> 

```jsx
const express = require("express");
const morgan = require("morgan");
const app = express();
app.use(express.static());
app.use(express.urlencoded({extended : true})); // {extended : true} help to use more complex data type like arrays
app.use(morgan("tiny")); // "tiny" is way to print small log ,,, you can also store logs in file
```


## Environments

>  environment variables : are variable that set on running
> 

> `app.get(”env”)` : return the current environment working on it like development or production .
> 

```jsx
app.get("env"); // return NODE_ENV
```

## configuration


> #### 🔥 config : is package that help us to set environment variable for configuration

### steps to create you configs

1. create config directory and put your json file configs based on NODE_ENV

    ![Untitled](https://github.com/ahmedeid6842/cheat-sheet/assets/57197702/59c8983e-ed55-435b-88b5-b29170e0f144)

2. type a json object to set props 

    ![Untitled](https://github.com/ahmedeid6842/cheat-sheet/assets/57197702/c0f28c35-03c5-4d87-b244-a538bee20c9b)

3. access the env you assigned 

    ```jsx
    const config = require("config");
    console.log(config.get("name"));
    ```

    > #### 🔥 if you want to set secret env_var but not write it in json object source code config package provide custom_environment_variables.json to set those type of env
