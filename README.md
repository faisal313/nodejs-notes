# Nodejs Cheat-Sheet for Beginners

## What is Node.js ?
Node.js is an open-source, cross-platform, JavaScript runtime environment that executes JavaScript code on the Server.

## Why Node.js ?
```code
Node.js uses asynchronous programming!
```

A common task for a web server can be to open a file on the server and return the content to the client.

Here is how PHP or ASP handles a file request:

Sends the task to the computer's file system.
Waits while the file system opens and reads the file.
Returns the content to the client.
Ready to handle the next request.

#### Here is how Node.js handles a file request:

***Sends the task to the computer's file system.
Ready to handle the next request.
When the file system has opened and read the file, the server returns the content to the client.
Node.js eliminates the waiting, and simply continues with the next request.
Node.js runs single-threaded, non-blocking, asynchronously programming, which is very memory efficient.***


## Nodejs is best to use:

- Rest API

- Realtime applications

- Microservices

- CRUD applications (blog/shopping cart)

- Tools and Utilities (command line tools as an example)



there are core module like:

- path

- os (Operating System)

- fs (File System)



to use them, you will call them in a variable (mostly they will be constants, whose value can be re-assigned)

```javascript
const path = require('path');
```

you can also import functions that are exported to other javascript files to use them

```javascript
const myfile = require('./myfile');
```



## Starting a Nodejs project

you will start by creating a ```package.json``` file using:

```javascript
npm init 

npm init -y //this will automatically set to defaults without asking questions
```



if you are using a specific project on another device, you can install all of your dependencies by using 

```javascript
npm install
```

there are also dev dependencies, these dependencies only work on development enviroment not on production



to install a dependency as a dev dependency

```javascript
npm install -D nodemon
```

if you want to use elements inside of another file, you can export it

```javascript
const person = {
    name: 'John Doe',
    age: 30
}
module.exports = person;
```

then you can import it in another file

```javascript
const person = require('./person');
```

you can also export classes and functions as well

```javascript
class Person {
    constructor(name, age){
        this.name = name;
        this.age = age;
    }
    greeting(){
        console.log(`My name is ${this.name} and I am ${this.age}`);
    }
}
module.exports = Person;
```

then you can import it and use it

```javascript
const Person = require('./person');
const person1 = new Person('John Doe', 30);

person1.greeting(); // My name is John Doe and I am 30
```

keep in mind that nodejs doesn't support ES6 importing

```javascript
import Person from './person'
```

you have to use BabelJS or Typescript and see what is backwards compatible to ES5

## path Module

```javascript
const path = require('path');
```

to get the name of the file (base filename)

```javascript
path.basename(__filename) //path.js
```

to get the directory name

```javascript
path.dirname(__filename) // /users/myPc/nodeFile/pathFile
```

to get the file extension

```javascript
path.extname(__filename) // .js
```

to create a path object

```javascript
path.parse(__filename)

// it will generate this object
{
    root: '/',
    dir: '/users/myPc/nodeFile/pathFile',
    ext: '.js',
    name: 'path'
}
```

since it is an object so you can use any part of it



to concatenate paths

```javascript
path.join(__dirname, 'test', 'hello.html')

// it will create a path like this:
// /users/myPc/nodeFile/pathFile/test/hello.html
```



## Operating System Module (os)

```javascript
const os = require('os');
```

to get the platform

```javascript
os.platform()

// darwin for macOS and win32 for windows
```

to get CPU architecture

```javascript
os.arch()
// it will return cpu architecture for example- x64
```

to get CPU core info

```javascript
os.cpus()

// it will return a big object with complete cpu information
```

to get free available memory

```javascript
os.freemem()

// 122388480
```

to get total memory

```javascript
os.totalmem()

//34359738368
```

to get the home directory

```javascript
os.homedir()

// /users/myPc
```

to get uptime (time the system has been up)

```javascript
os.uptime()

// 1305116 (in seconds)
```



## Event Emitter Module

```javascript
const EventEmitter = require('events');
```

first create a class 

```javascript
class MyEmitter extends EventEmitter {}
```

initialize an object

```javascript
const theEmitter = new MyEmitter();
```

create an event listner

```javascript
theEmitter.on('event', () => console.log('Event!'));
```

initialize an event

```javascript
theEmitter.emit('event');

// Event!
```

##### Owner: Mohammad Faisal Khan
