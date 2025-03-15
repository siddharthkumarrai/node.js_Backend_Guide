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
```javascript
```diff
+require('dotenv').config()
const express = require('express')
const app = express()
const port = process.env.PORT

app.get('/', (req, res) => {
  res.send('jai shri ram!')
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```

