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

## PUT Request

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

## Configuration


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

# section 4 : Asynchronous Javacript

## Asynchronous VS Synchronous

> #### 🔥 Synchronous is executing the code line by line in blocking way blocking means block the thread until the current process is executed


> #### 🔥 Asynchronous is non-blocking executing means release the thread to execute another process and the back


![Untitled](https://github.com/ahmedeid6842/cheat-sheet/assets/57197702/f03f0355-93a7-4f92-ae2e-e93a92e6947c)

> in code below js engine will execute print before and release thread in setTimeout execute the another print then after two second will execute settime out
> 

```jsx
console.log("before");
setTimeout(()=>{
	console.log("reading a user from db");
},2000)
console.log("after");
```

## callback

> #### 🔥 callback means after executing this Async code do something

```jsx
const user = getUser(id);
console.log(user) // will print undefined 

function getUser(id){
	setTimeout(()=>{
		console.log("reading a user from db");
		return {id, name:"ahmed eid"};
	},2000)
}
```

> ⬆️ In code above even `getUser`  have Async function but it’s executed as Sync function so it return undefined because in execution time it doesn’t return anything 
> 


##### To solve the problem above of sync function have Async function we use callback

```jsx
getUser(1,(user)=>{
	console.log(user);
})

function getUser(id,callback){
	setTimeout(()=>{
		console.log("reading a user from db");
		callback({id,name:"ahmed eid"});
	},2000)
}
```

> ##### 🔥 callback cause a problem named callback hell which mean a callback executed inside another callback and so on

```jsx
getUser(1,(user)=>{
	getaddress(user,(address)=>{
			console.log(user,address);
	})
})

function getUser(id,callback){
	setTimeout(()=>{
		console.log("reading a user from db");
		callback({id,name:"ahmed eid"});
	},2000)
}

function getaddress(user,callback){
	setTimeout(()=>{
		callback(["egypt","ismailia"]);
	})
}
```

## Promises

##### 🔥 promises hold the event result of Async operation

> ##### promises have 3 status : pending - fulfilled - rejected 
1. pending means the promises is processing 
2. fulfilled means async operation execution is done and return result 
3. rejected means Async operation rejected and return error
> 

![Untitled](https://github.com/ahmedeid6842/cheat-sheet/assets/57197702/34700e78-b4c6-4371-9972-a0c19fbde2d8)

```jsx
const p = new Promise((resolve,reject)=>{
	// code that executed async
	resolve(result);
	reject(new Error("error message"));
})
```

```jsx
const p = new Promise ((resolve,reject)=>{
	setTimeout(()=>{
		resolve({name:"ahmed eid"}) // after this async code is executed it will return object
	},2000)
})

p.then((result)=>console.log(result)); //consuming the promise 
```

### Examples

```jsx
getUser(1)
    .then((user) => getAdresses(user))
    .then((address) => console.log(address));

function getUser(id) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve({ id: id, name: "ahmed eid" });
        }, 2000);
    })
}

function getAdresses(username) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(["egypt", "isamilia"]);
        }, 2000)
    })
}
```

## Settled Promises

> ##### if you want to set promise that is already resolved . we use this case in testing
> 

```jsx
const p = Promise.resolve({id:1,name:"ahmed eid"});
p.then((result)=>console.log(result));
```

## Parallel Promises

> #### if we want to return the result only if the multiple promises is executed correctly . we use `all(array)`
> 

```jsx
const p1 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve({ id: 1, name: "ahmed eid" });
    }, 2000);
})

const p2 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve({ id: 2, name: "mohamed ahmed" });
    },4000)
})

Promise.all([p1, p2])
    .then(result => { console.log(result) }); // print the result after 4 second  
```

> #### if we want to return the result if one of the multiple promises is executed correctly . we use `race(array)`
> 

```jsx
const p1 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve({ id: 1, name: "ahmed eid" });
    }, 2000);
})

const p2 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve({ id: 2, name: "mohamed ahmed" });
    },4000)
})

Promise.race([p1, p2])
    .then(result => { console.log(result) }); // print the result after 2 second  
```

# section 5 : CRUD operation using Mongodb

#### 🔥 mongoose : is npm package that help us to work with mongodb

## Connect To MongoDB Server

> connect to mongodb using mongoose package through `connect()` function
> 

```jsx
const mongoose = require("mongoose");

mongoose.connect("mongodb://localhost/dbName")
					.then(()=>console.log("connected successfully"))
					.catch((err)=>console.log(err.message));
```

## Schema

> schema is to set the schema of your object of documents that will be stored in Database
> 

```jsx
const mongoose= require("mongoose");

const schema = new mongoose.Schema({
	prop1 : String ,
	prop2 : Number ,
})
```

> ##### we have different data Type in mongodb schema
> 

![Untitled](https://github.com/ahmedeid6842/cheat-sheet/assets/57197702/ae299061-0228-4504-9252-c6c15bd5e4c0)

## Model

> model is about to create class or collection in you DB based on schema you defined
> 

```jsx
const mongoose= require("mongoose");

const schema = new mongoose.Schema({
	prop1 : String ,
	prop2 : Number ,
})

const Course = mongoose.model("tableName",schema);
```


> we can define a new instance of model and save it
> 

```jsx
const mongoose= require("mongoose");

const schema = new mongoose.Schema({
	prop1 : String ,
	prop2 : Number ,
})

const Course = mongoose.model("tableName",schema);

const course = new Course({ // creating a new instance of Course model
			prop1: "value",
			prop2 : 5 
})

await course.save(); // to save this course in db

```

## Query

> `find()` :is query use to find document from DB .
`sort({prop : 1})` : sort returned document based on prop  if prop:1 means ascending else prop:-1 then it's descending order >
`select({prop1 : 1 , prop2 : 2})` : select specified prop from the returned document .
> 

```jsx
function Query(){
	const course = await Course.find({name:"value"})
								.limit(10)
								.sort({name:1}) // if name:1 means ascending else name:-1 then it's descending order
								.select({name:1 , phone : 1}); // select specified prop from return docuemnt 
}
```

> #### we can define a new instance of model and save it
> 

```jsx
const mongoose= require("mongoose");

const schema = new mongoose.Schema({
	prop1 : String ,
	prop2 : Number ,
})

const Course = mongoose.model("tableName",schema);

const course = new Course({ // creating a new instance of Course model
			prop1: "value",
			prop2 : 5 
})

await course.save(); // to save this course in db

```


> #### 🔥 Schema : isn’t just important to insert the data but it’s very important to create if you will use query operator it tell query type of property that it’s search on


## Query (comparison & logical) operator

**1. comparison operator** 
    `eq`: equal 
    `ne`: not equal 
    `gt`: greater than 
    `gte`: greater than or equal 
    `lt`: less than 
    `lte`: less than or equal 
    `in[value1,value2]` : prop in one of given values 
    `nin[value1, value2]` : rever of in

    ```jsx
    async function Query(){
        const course =await Course.find({price:{$gt : 10}}) //find a prices document where price is greater than 10 
    }
    ```



**2. logical operator** 
    `and([{},{}])` : (condition1 & condition2) are true 
    `or([{},{}])` : (condition1 | condition2) are true

    ```jsx
    async function Query(){
        const course = await Course.find()
                                    .or([{price : 10},{isPublished:true}]) // price = 10 or ispublished=true
    }
    ```

> `count()` : count the document and return them
> 

```jsx
async function Query(){
	const course = await Course.find()
								.or([{price : 10},{isPublished:true}])
								.count(); // this query will return the count of document that staticfy the condtion 
}
```

## Pagination

> #### return number of document in each page 
#### `.skip((pageNumber -1)*pageSize).limit(pageSize);`
> 

```jsx
async function Query(){
	const course = await Course.find()
							    .skip((pageNumber - 1)* pageSize)
								.limit(pageSize);
}
```

## Updating

> #### `findOneAndUpdate({ prop1 : value},{$set:{ prop2:value , prop3 : value}})` : find document based on prop1 and update based on $set
> 

```jsx
const mongoose = require("mongoose");

mongoose
    .connect("mongodb://localhost/mongo-exercises")
    .then(() => console.log("connected successfully to database"))
    .catch((err) => console.log(err.message));

const Course = mongoose.model("course", new mongoose.Schema({
    name: String,
    isPublished: Boolean,
    price: Number,
    tags: [String]
}));

async function exercise(id) {
    const course = await Course.findOneAndUpdate({ name: "Express.js Course" }, {
        $set: {
            price : 50
        }
    }, { new: true });
    console.log(course);

}

exercise("5a68fde3f09ad7646ddec17e");
```

## Exercise 1

![Untitled](https://github.com/ahmedeid6842/cheat-sheet/assets/57197702/704cc939-4fb3-4169-8d3c-155208123714)

```jsx
const mongoose = require("mongoose");

mongoose
    .connect("mongodb://localhost/mongo-exercises")
    .then(() => console.log("connected successfully to database"))
    .catch((err) => console.log(err.message));

const Course = mongoose.model("course", new mongoose.Schema({
    name: String,
    isPublished: Boolean,
    tags: [String]
}));

async function exercise() {
    const course = await Course.find({ isPublished: true, tags: "backend" })
        .sort({ name: 1 });
    console.log(course);
}

exercise();
```

## Exercise 2

![Untitled](https://github.com/ahmedeid6842/cheat-sheet/assets/57197702/44185f3d-11d7-45fa-98e0-89fdc285bf65)

```jsx
const mongoose = require("mongoose");

mongoose
    .connect("mongodb://localhost/mongo-exercises")
    .then(() => console.log("connected successfully to database"))
    .catch((err) => console.log(err.message));

const Course = mongoose.model("course", new mongoose.Schema({
    name: String,
    isPublished: Boolean,
    tags: [String]
}));

async function exercise() {
    const course = await Course.find({ isPublished: true, tags: { $in: ["backend", "frontend"] } })
        .sort({ price: -1 })
        .select({ name: 1, author: 1 });
    console.log(course);
}

exercise();
```

# Section 6 : Mongoose Data validation

> #### We can make field required based on the existence of another field
> 

```jsx
const schema = new mongoose.Schema({
	name : {
		type : String 
	},
	isPublished : {
		type : Number, 
		required : function(){return this.name}
	}
})
```

> #### In string Data Type we can set minimum length and maximum length of field
> 

```jsx
const schema = new mongoose.Schema({
	name : {
		type : String ,
		minlength : 5,   //minimum length of name field is 5 and maximum is 255
		maxlength : 255
	}
})
```

> #### We can defined specific values and our field must be one of those values
> 

```jsx
const schema = new mongoose.Schema({
	name:{
		type : String , 
		enum : ["ahmed","mohamed","hassan"] // our name field should be one of those values in array
	}
})
```

> #### We can trim “remove padding our extra spaces from front and the end of string” .
we can make mongoose automatically convert our field to lowercase or uppercase
> 

```jsx
const schema = new mongoose.Schema({
	name:{
		type : String,
		trim : true , 
		lowerCase : true // will convert our string to lowercase even we insert it as upper case 
	}
})
```

> #### we can define setter and getter that specify how to get and set value of property
> 

```jsx
const schema = new mongoose.Schema({
	phone : {
		type : Number , 
		get : (value) => Math.round(value),
		set : (value) => Math.round(value)
	}
})
```

# Section 7 : Modeling Relationship

#### 🔥 we have two types of relationship in mongodb : 
  1. using references “Normalization” : `course {author:{_id:”123213687687”}}`
  2. using embedded “denormalization” : `course {author:{name:”ahmed”, age:25}}`


#### 🔥 references and embedded using are trad-off between performance and consistency .
> means in reference modeling if author name has change it’s automatically changed in all documents that reference author document, but it’s very heavy process to move from one collection to another . **consistence > performance** 
but in embedded modeling if author name has changed so you have to change it manually in all document that embed that document, but it’s easy to get author because it’s in the same collection . **performance > consistence**
>

## Define embedded and reference modeling

```jsx
//define embedded 
const mongoose = require("mongoose");
const AuthorSchema = new mongoose.Schema({
    name: String,
    bio: String,
    websit: String
})
const Author = mongoose.model("Author", AuthorSchema);

const Course = mongoose.model("course", new mongoose.Schema({
    name: String,
    author: {
        type: AuthorSchema, // we embedd author document 
        required: true
    }
}))

//define reference 
const AuthorSchema = new mongoose.Schema({
    name: String,
    bio: String,
    websit: String
})
const Author = mongoose.model("Author", AuthorSchema);

const Course = mongoose.model("course", new mongoose.Schema({
    name: String,
    author: {
        type: mongoose.Schema.Types.ObjectId, // we refernce the author document 
        ref: "Author"  // set in which collection that document is
    }
}))

```

## Population

> population is used with reference modeling .
in case if we want to get actual document which we refer .
> 

```jsx
const courses = await Course.find()
							.populate("author","name -_id"); // means get the actual document which we refer with author property, "name -_id" if you want to select specific props
```

## Update embedding document

```jsx
async function updateEmbed(){
	const course = await Course.find({name:"firstCourse"});
	course.author.name = "new author name";
	await course.save();
}

//another technique 
async function updateEmbed(){
	const course = await Course.update({name:"firstCourse"},{
			$set:{
				"author.name" : "new author name"
			}
	})
}
```

## Transaction fawn

> transaction means that if have two process and both of them should be executed
> 

> fawn : is npm package that help us to do transaction
> 

```jsx
const Fawn = require("fawn");
Fawn.init(mongoose)
async function doSomeThing(){
    new Fawn.task()
		.save("collectionName",object to store)
		.update("collectionName",{_id:movie.id},{$inc:{numberInStock : -1}}); // those two processes "save and update" both of them will execute and if one fail the anoterh is fail too 
}
```

# Section 8 : Authentication and Authorization

## Register Method

#### register route have four main stages :
  1. validate request body 
  2. check email is unique 
  3. hash password
  4. save your new user

```jsx
route.post("/", async (req, res) => {
		//1. validate request body
    const { error } = validateUser(req.body);
    if (error) return res.status(400).send(error.message);

		//2. check if email is unique 
    let user = await User.findOne({ email: req.body.email });
    if (user) return res.status(400).send("email already exsist");
    
    user = new User(req.body);

		//3. hash password 
    const salt = await bcrypt.genSalt(10);
    user.password = await bcrypt.hash(user.password, salt);
    
		//4. save our user 
    await user.save();

    return res.send(_.pick(user, ["name", "email"]));
})
```

## Login Method

#### login route have four main stages :
  1. validate request body 
  2. check email is exist or not 
  3. compare entered password with hashed password
  4. return JSON WEB TOKEN

```jsx
route.post("/", async (req, res) => {
		//1. validate request body
    const { error } = validateUser(req.body);
    if (error) return res.status(400).send(error.message);

		//2. check email is exist or not 
    let user = await User.findOne({ email: req.body.email });
    if (!user) return res.status(404).send("email not found or incorrect password");

		//3. compare entered password with hashed password
    const verified = await bcrypt.compare(req.body.password, user.password);
    if (!verified) return res.status(404).send("email not found or incorrect password");

		//4. return JSON WEB TOKEN
    return res.send(jwt.sign({ _id: user._id }, "secret"));
})
```

## Is Authenticated middleware

#### isAuth middleware is to check if the user is authenticated or not .
#### this method has four main steps : 
  1. check if token provided 
  2. verify the token , if not valid return 400 status “bad request”
  3. assign `req.user = decoded` to use payload in the next stages
  4. pass the control to the next middleware in request process pipeline

```jsx
const jwt = require("jsonwebtoken");
module.exports = function (req, res, next) {
		// 1. check if token provided 
    const token = req.header("x-auth-token");
    if (!token) return res.status(401).send("no token provided");

    try {
				// 2. verify the token , if not valid return 400 status “bad request”
        let decode = jwt.verify(token, "secret");
        if (!decode) return res.status(400).send("invalid token provided");
				
				// 3. assign req.user = decoded to use payload in the next stages
        req.user = decode;

				// 4. pass the control to the next middleware in request process pipeline
        next();
    } catch (err) {
        return res.send(err.message);
    }
}
```

## Is Authorized  middleware

#### isAuthorized middleware is to check if the user is authorized or not .
#### method steps : 
  1. check if an `req.user` payload  is Admin is set to true or not, if not return 403 status “un authorized”
  2. pass the control to the next middleware
> 

```jsx
module.exports = function (req, res, next) {
    if (!req.user.isAdmin) return res.status(403).send("un authorized");
    next();
}
```

## Bcrypt

#### 🔥 bcrypt : is npm package that hash and verify password

> 👀 salt is very important cause it prevent reversed testing 
`genSalt(numberOfRounds)` : this bcrypt method create salt based on number of rounds , the more number of round increase the more it become complex hash but the more it consuming time .
`hash(plaintext,salt)` : this function takes our plain text and salt arguments and return hashed password
> 

```jsx
const bcrypt = require("bcrypt");

async function createPassword(password){
	const salt = await bcrypt.genSalt(10);
	const hashedpassword = await bcrypt.hash(password,salt);
	console.log(hashedpassword);
}

createPassword();
```

> 👀 `compare(plaintext,hashedPassword)` : a bcrypt method that takes plaintext and hashed password , return true of false based on the correctness of password
> 

## JSON Web token


🔥 what is JWT ?? [https://jwt.io/introduction](https://jwt.io/introduction)

> #### 👀 jsonwebtoken : is npm package to create json web token and verify it although
> 

> `sign(data,secret)` : jwt method that create json web token
> 

> `verify(token,secret)` : jwt method that verify if the token is correct based on secret , if true it’s return the payload of token
> 

```jsx
const jwt = require("jsonwebtoken");

async function createjwt(data){
	const jwt = jwt.sign(data,"jwtsecret"); //create jwt that contains "data" in payload with secret = "jwtsecret"
	console.log(jwt);
}

createjwt({name : "ahmed"});
const decoded = jwt.verify(createjwt({name : "ahmed"}),"jwtsecret"); // return {name : "ahmed"}
```