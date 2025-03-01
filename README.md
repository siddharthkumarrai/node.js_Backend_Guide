# NODE.JS BACKEND
1.) a web and mobile-based application that interacts with a backend system and a remote database.
```node.js
+---------+       +---------+       +---------+       +----------------+
| Browser | <--> |  API    | <--> | Backend | <--> |     DB         |
+---------+       +---------+       +---------+       | Another       |
                                                      | Continent     |
+---------+       +---------+       +---------+       +----------------+
| Mobile  | <--> |  API    | <--> | Backend | <--> |     DB         |
+---------+       +---------+       +---------+       | Another       |
                                                      | Continent     |
                                                      +----------------+
```
graph TD;
    Browser-->API;
    Mobile-->API;
    API-->Backend;
    Backend-->DB;
    DB-->Another_Continent;


