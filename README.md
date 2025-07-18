# Backend Development

## 2 major components

### A Programming Language
- Java, JS, PHP, golang
- C++
- on a framework

### A Database
- Mongo, MySQL
- Postgres, sqlite
- ORM, ODM

1.) a web and mobile-based application that interacts with a backend system and a remote database.
```node.js
+---------+       +---------+       +---------+       +----------------+
| Browser | <--> |  API    | <-->   | Backend | <-->  |     DB         |
+---------+       +---------+       +---------+       | Another        |
                                                      | Continent      |
+---------+       +---------+       +---------+       +----------------+
| Mobile  | <--> |  API    | <-->   | Backend | <-->  |     DB         |
+---------+       +---------+       +---------+       | Another        |
                                                      | Continent      |
                                                      +----------------+
```
## Project Structure

→ **Src**
  * index
    → DB connects
  * App
    → config, cookie, urlEncode
  * constants
    → enums, DB-name

→ **DB**

→ **Models**

→ **Controllers**

→ **Routes**

→ **Middlewares**

→ **Utils**

# Express Server Architecture
![Alt Text](https://res.cloudinary.com/dnknslaku/image/upload/w_400,h_300/v1742054467/Screenshot_2025-03-15_211052_rjgr3c.png)

## setting up your Node.js backend
1. Install Node.js and npm
2. Create a Project Directory
3.  initialize a Node.js project
 ```node.js
 npm init
 ```
> index.js
```javascript
console.log("siddharth")
```
> package.json
```json
"scripts":{
    "start": node index.js"
}
```
### To run index.js file
```node.js
$ npm run start
```

## install express
```node.js
$ npm install express
```
> index.js
```javascript
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.send('jai shri ram!')
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
``` 
## install dot env
```terminal
$ npm install dotenv
```
- making .env file in root directory
> .env
```javascript
PORT=4000
```
> index.js
```diff
- require('dotenv').config()
const express = require('express')
const app = express()
- const port = process.env.PORT

app.get('/', (req, res) => {
    res.send('jai shri ram!')
})

app.listen(port, () => {
    console.log(`Example app listening on port ${port}`)
})
```
 ## 2 Types of Import in Node.js
 1.  CommonJS (require)
- Node.js ka default module system hai.
- Yeh synchronous hota hai (blocking).
- module.exports ke saath export hota hai.
👉 file1.js (Export)
```javascript
const greet = () => {
  console.log('Hello from CommonJS!');
}

module.exports = greet;
```
👉 file2.js (Import)
```javascript
const greet = require('./file1');
greet(); // Output: Hello from CommonJS!
```
2. ES Modules (import/export)
- Modern JavaScript ka module system hai.
- Yeh asynchronous hota hai (non-blocking).
- "type": "module" ko package.json me set karna padta hai ya .mjs extension use karni         padti hai.
👉 file1.mjs (Export)
```javascript
export const greet = () => {
  console.log('Hello from ES Modules!');
}
```
👉 file2.mjs (Import)
```javascript
import { greet } from './file1.mjs';
greet(); // Output: Hello from ES Modules!
```

## How to connect frontend and backend in javascript 
> backend/server.js
```javascript
import express from 'express';

const app = express();

app.get('/',(req,res)=>{
    res.send("server is ready");
});

const port = process.env.PORT || 3000

app.listen(port,() => {
    console.log(`server at https://localhost:${port}`}
    }
);
```
> fronted
```terminal
PS D:\fullstack\frontend> npm create vite@latest .
```
> frontend/src/app.jsx
```react.js
function App() {
  const [userData, setUserData] = useState([]);
  return (
    <>
      <h1>userData</h1>
      <p>{userData.length}</p>
      {userData.map((user) => {
        <div key={user.id}>
          <h2>{user.name}</h2>
          <p>{user.email}</p>
          <p>{user.city}</p>
        </div>;
      })}
    </>
  );
}

export default App;
```
## install axios
```node
$ npm i axios
```
```react.js
import { useState, useEffect } from "react";
import axios from "axios";

function App() {
  const [userData, setUserData] = useState([]);

  useEffect(() => {
    axios
      .get("http://localhost:3000/api/userdata")
      .then((response) => {
        setUserData(response.data);
      })
      .catch((error) => {
        console.log(error);
      });
  });

  return (
    <>
      <h1>userData</h1>
      <p>{userData.length}</p>
      {userData.map((user) => {
        <div key={user.id}>
          <h2>{user.name}</h2>
          <p>{user.email}</p>
          <p>{user.city}</p>
        </div>;
      })}
    </>
  );
}

export default App;

```
- console error ( CORS )
  -  1. Whitelisting in server
     2. add PROXY
```diff
- Access to XMLHttpRequest at 'http://localhost:3000/' from origin 'http://localhost:5173' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.
```
## PROXY ( api Standardization , .get("/api/userdata") )
```diff
  useEffect(() => {
    axios
      .get("/api/userdata")
      .then((response) => {
        setUserData(response.data);
      })
      .catch((error) => {
        console.log(error);
      });
  });
```
- error
```diff
- GET https://localhost:5173/api/userdata  404 (Not Found)
```
> vite.config.js
```javascript
export default defineConfig({
  server: {
    proxy: {
      "/api": "https://localhost:3000",
    },
  },
});
```
# Data Modeling/ Object Modeling Tools
<table>
  <thead>
    <tr>
      <th>Tool</th>
      <th>Type</th>
      <th>Best For</th>
      <th>Free Version</th>
      <th>Platforms</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>Moon Modeler</b></td>
      <td>Schema Designer</td>
      <td>MongoDB, Firestore, DynamoDB</td>
      <td>✅</td>
      <td>Windows, Mac</td>
    </tr>
    <tr>
      <td><b>Hackolade</b></td>
      <td>Schema Designer</td> 
      <td>MongoDB, DynamoDB, Cassandra</td>
      <td>✅ (Limited)</td>
      <td>Windows, Mac</td>
    </tr>
    <tr>
      <td><b>dbdiagram.io</b></td>
      <td>Code-based</td>
      <td>MongoDB</td>
      <td>✅</td>
      <td>Web</td>
    </tr>
    <tr>
      <td><b>Draw.io</b></td>
      <td>Diagram Builder</td>
      <td>Tree-based model</td>
      <td>✅</td>
      <td>Web</td>
    </tr>
    <tr>
      <td><b>MongoDB Compass</b></td>
      <td>Data Explorer</td>
      <td>MongoDB</td>
      <td>✅</td>
      <td>Windows, Mac, Linux</td>
    </tr>
    <tr>
      <td><b>Archi</b></td>
      <td>Diagram Builder</td>
      <td>Firebase, DynamoDB</td>
      <td>✅</td>
      <td>Windows, Mac, Linux</td>
    </tr>
    <tr>
      <td><b>Studio 3T</b></td>
      <td>Schema Designer</td>
      <td>MongoDB</td>
      <td>Free Trial</td>
      <td>Windows, Mac, Linux</td>
    </tr>
    <tr>
      <td><b>NoSQL Workbench</b></td>
      <td>Data Modeler</td>
      <td>AWS DynamoDB</td>
      <td>✅</td>
      <td>Windows, Mac</td>
    </tr>
  </tbody>
</table>

# MongoDB Todo Application Schema

This document provides a visual representation of the database schema and relationships for the Todo application using Mermaid.

## Entity-Relationship Diagram
```mermaid
graph LR 
    User[("User
    ---
    _id: ObjectId
    username: String
    email: String
    password: String
    createdAt: DateTime
    updatedAt: DateTime")]

    Todo[("Todo
    ---
    _id: ObjectId
    content: String
    complete: Boolean
    createdBy: ObjectId
    subTodos: ObjectId[]
    createdAt: DateTime
    updatedAt: DateTime")]

    SubTodo[("SubTodo
    ---
    _id: ObjectId
    content: String
    complete: Boolean
    createdBy: ObjectId
    createdAt: DateTime
    updatedAt: DateTime")]

    User -->|1:N| Todo
    Todo -->|1:N| SubTodo
```

## Boilerplate code of models ( schema )
```javascript
import mongoose from "mongoose"

const todoSchema = new mongoose.Schema({},{timestamps: true})

export const Todo = mongoose.model("Todo", todoSchema);
```

> user.models.js
```javascript
import mongoose from "mongoose"

const userSchema = new mongoose.Schema({
      username: {
         type: string,
         required: true,
         unique: true,
         lowercase: true
      },
      email: {
         type: String,
         required: true,
         unique: true,
         lowercase: true
      },
      password: {
         type: String,
         required: true
      }

   }, {timestamps: true}
}

export const User = mongoose.model("User", userSchema)
```
> sub_todo.models.js
```javascript
import mongoose from "mongoose"

const todoSchema = new mongoose.Schema({
   content: {
      type: String,
      required: true
   },
   complete: {
      type: Boolean,
      default: false
   },
   createdBy: {
      type: mongoose.Schema.Types.ObjectId,
      ref: "User",
   }
}, {
   timestamps: true
})

export const Todo = mongoose.model("Todo", todoSchema);
```
> todo.models.js
```javascript
import mongoose from "mongoose";

const todoSchema = new mongoose.Schema({
   content: {
      type: String,
      required: true,
   },
   complete: {
      type: Boolean,
      default: false
   },
   createdBy: {
      type: mongoose.Schema.Types.ObjectId
      ref: "User"
   },
   subTodos: [{
      type: mongoose.Schema.Types.ObjectId,
      ref: "SubTodo",
   }, ],
}, {
   timestamps: true
});

export const Todo = mongoose.model("Todo", todoSchema);
```
# Setup Production Ready Backend
- verify the node
```node
$node -v
```
- initialize a project
```node
$npm init
```
- track the empty folder
```node
$ mkdir public
$ cd public
$ mkdir temp
$ cd temp
$ touch .gitkeep
```
> public/temp/.gitkeep
- making gitignore file in root directory 
```node
$touch .gitignore
```
> .gitignore
```diff
- use .gitignore generator tools to boilerplate code
```
- making environment variable file in root
```
$ touch .env .env.sample 
```
> .env
> .env.sample
- root
```node
$mkdir src
```
> src
```node
$ touch index.js app.js constants.js
```
- install nodemon as a Dev dependency 
```node
$npm i -D nodemon
```
> package.json
```json
{
  "name": "backend",
  "version": "1.0.0",
  "description": "production ready backend",
  "main": "index.js",  
  "type": "module",                ☑️
  "scripts": {
    "dev": "nodemon src/index.js"  ☑️
  },
  "author": "siddharth kumar rai",
  "license": "ISC",
  "devDependencies": {
    "nodemon": "^3.1.9"
  }
}
```
> src
```node
$mkdir controllers db middlewares models routes utils
```
- install prettier
```node
$npm i -D prettier
```
- root
```node
$touch .prettierrc .prettierignore
```
> .prettierrc
```json
{
  "singleQuote": false,
  "bracketSpacking": true,
  "tabWidth": 2,
  "trailingComma": "es5"
  "semi": true
}
```
> .prettierignore
```json
/.vscode
/node_modules
./dist

*.env
.env
.env.*
```
## Database Connection 
### Two thing know to talk to database
#### use try catch
#### use async await
<h1 style="color: red;">Setup MongoDb Database</h1>

> .env
```node
PORT=8000
MONGODB_URI=mongodb+srv://<db_username>:<db_password>@cluster0.yjhd9gi.mongodb.net
```
> constants.js
```javascript
export const DB_NAME = "videotube"
```
- install dependency
```node
$npm i mongoose express dotenv
```
## DATABASE CONNECTION APPROACH 
#### APPROACH 1
  
> src/index.js
```javascript
import  mongoose from "mongoose";
import { DB_NAME } from "./constants";

import express from "express"
const app = express()

;( async () => {
      try{
          await mongoose.connect(`${process.env.MONGODB_URI}/${DB_NAME}`)
          app.on("error", (error) => {
              console.log("ERROR: ", error);
              throw error
          })
          app.listen(process.env.PORT, () => {
              console.log(`app is listening on port ${process.env.PORT}`);
          })
      } catch (error) {
          console.error("ERROR: ", error)
          throw err
      }
)()
```
#### APPROACH 2
> db/index.js
```javascript
import mongoose from "mongoose";
import {
   DB_NAME
} from "./constants";

const connectDB = async () => {
   try {
      const connectionInstance = await mongoose.connect(`${process.env.MONGODB_URI}/${DB_NAME}`)
      console.log(`\n MongoDB connected !! DB HOST: ${connectionInstance.connection.host} `);

   } catch (error) {
      console.log("MONGODB connection error ", error);
      process.exit(1)
   }
}
```
> src/index.js
```javascript
// require(`dotenv`).config({path: "./env"})
import dotenv from "dotenv
import connectDB from "./db";

dotenv.config({
    path: './env'
})

connectDB()
```
> package.json
```json
{
  "scripts": {
    "dev": "nodemon -r dotenv/config --experimental-json-modules src/index.js"  ☑️
  },
}
```
> src/app.js
```javascript
import express from "express"

const app = express()

expoert { app }
```
> src/index.js
```javascript
// require(`dotenv`).config({path: "./env"})
import dotenv from "dotenv
import connectDB from "./db";

dotenv.config({
    path: './env'
})

connectDB()  
.then(()) => {                                                            ☑️
    app.listen(process.env.PORT || 8000, () => {
        console.log(`server is running at port : ${process.env.PORT}`);
    }
}
.catch((error) => {
    console.log("MONGO db connection failed !!! ", error);
)
```
- install dependency
```node
$npm i cookie-parser cors
```
> src/app.js
```javascript
import express from "express"
import cors from "cors"
import cookieParser from "cookie-parser"

const app = express()

app.use(cors({
    origin: process.env.CORS_ORIGIN,
    credentials: true
))

app.use(express.json({limit: "16kb"}))   // handle data like form data (data from body)
app.use(express.urlencoded({extended: true, limit: "16Kb"})) // handle url space convert %20
app.use(express.static("public"))
app.use(cookieParser())

expoert { app }

```
> utils/asynchandler.js
```javascript
- method 1
const asyncHandler = (requestHandler) => {
    (req,res,next) => {
        promise.resolve(requestHandler(req,res,next)).catch((err) => next(err))
    }
}

export {asyncHandler}



- method 2
const asyncHandler = (fn) => async (req,res,next) => {
    try {
        await fn(req,res,next)
    } catch (error) {
        res.status(error.code || 500).json({
            success: false,
            message: error.message
        })
}
```
> utils/ApiError.js
```javascript
class ApiError extends Error {
    constructor(statusCode, message = "Something went wrong", errors = [], stack = ""){
        super(message)
        this.statusCode = statusCode
        this.data = null
        this.message = message
        this.success = false;
        this.errors = errors

        if (stack) {
            this.stack = stack
        } else{
            Error.captureStackTrace(this, this.constructor)
        }
    }
}
```
> utils/ApiResponse
```javascript
class ApiResponse {
    constructor(statusCode, data, message = "Success"){
        this.statusCode = statusCode
        this.data = data
        this.message = message
        this.success = statusCode < 400
    }
}
```
