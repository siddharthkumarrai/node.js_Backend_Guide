# NODE.JS BACKEND
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
```mermaid
graph TD;
    A[Computer/Mobile] -->|GET Request| B[Server];
    B -->|Response via Express| A;
    B -->|Listen| C[Routes];
    C -->|/ Home Route| D[Home Handler];
    C -->|/login Login Setup| E[Login Handler];
```
## setting up your Node.js backend
1. Install Node.js and npm
2. Create a Project Directory
3.  initialize a Node.js project
   
 ```node.js
        npm init
 ```
4. Install Dependencies
- for example:- 
```node.js
npm install express
```

