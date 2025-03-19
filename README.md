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
## Boilerplate code of models ( schema )
> user.models.js
```javascript
import mongoose from "mongoose

const userSchema = new mongoose.Schema({
username: {
  type: string,
  required: true
}
},{timestamps: true}}

export const User = mongoose.model("User",userSchema)
```
