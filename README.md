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

```mermaid
flowchart LR
    client["Computer<br>Mobile"] -->|"get"| server["server"]
    server -->|"Express"| client
    
    subgraph server_config["Server Configuration"]
        direction TB
        listen["listen"]
        home["/ : home route"]
        login["/login : login setup"]
    end
    
    subgraph database["Database"]
        mongoose["mongoose"]
    end


    
→ **More (depends)**
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

