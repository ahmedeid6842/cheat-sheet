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