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

