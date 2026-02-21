# Lab 2 - CST8915: 12-Factor Refactoring & Multi-VM Deployment

**Student Name:** Harshdeep uri

**Course:** CST8915 - Full-stack Cloud-native Development

## Demo Video
https://youtu.be/eMdVzz2MLUA
---

##  Service Repositories

Each microservice  comply with the **Codebase** factor of the 12-Factor App methodology.

1. **Order Service (Node.js):** https://github.com/harshdeep1230/order-service-lab2
2. **Product Service (Rust):**  https://github.com/harshdeep1230/product-service-lab2
3. **Store Front (Vue.js):**  https://github.com/harshdeep1230/store-front-lab2

---

## Reflection Questions
Describe what you did to the order-service and product-service to conform to the Configurations and Backing Services factors?
To achieve the Configuration factor, I did not use hard-coded URLs and ports in the source code. I used dotenv library in the node.js environment and dotenv crate in the Rust environment to read the environment variables in a .env file during runtime. In the Backing Services, I altered the order-service to consume RabbitMQ as an attached resource by providing its connection string (with the Azure VM IP and credentials) as an environment variable rather than proving the local loopback address.

## What is the rationale of relying on environment variables, as opposed to hard-coding settings in your application?
It is portable as well as secure with the help of the environment variables. When it is hard-coded it makes it difficult to move the app to the different environments (development, staging, production) without affecting the source code and recompiling. Environment variables could be used to alter the settings of the database or broker profane. It also prevents the checking of sensitive credentials like passwords of RabbitMQ to version control.

## What is the reason why the individual repositories of each microservice are needed? What is this useful in supporting scaling and independence?
Factor 1 Codebase: Codebase is implemented in distinct repositories, whereby there is 1-to-1 relationship between a repository and a service. This freedom lets the teams use different technology stacks (e.g. Rust in one service and Node.js in another) without versioning interactions. It is scalable and deployable as well.
