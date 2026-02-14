# Lab 2 - CST8915: 12-Factor Refactoring & Multi-VM Deployment

**Student Name:** Harshdeep uri

**Course:** CST8915 - Full-stack Cloud-native Development

## Demo Video

---

##  Service Repositories

Each microservice  comply with the **Codebase** factor of the 12-Factor App methodology.

1. **Order Service (Node.js):** https://github.com/harshdeep1230/order-service-lab2
2. **Product Service (Rust):**  https://github.com/harshdeep1230/product-service-lab2
3. **Store Front (Vue.js):**  https://github.com/harshdeep1230/store-front-lab2

---

## 📝 Reflection Questions

### 1. What changes did you make to the order-service and product-service to comply with the Configurations and Backing Services factors?


In order to meet the Configuration factor, I eliminated the hard-coded URLs and ports in the source code. I combined the dotenv library in Node.js and dotenv crate in Rust to read environment variables in a .env file at runtime. In the case of Backing Services, I modified the order-service to use RabbitMQ as an attached resource by passing its connection string (with the Azure VM IP and credentials) as an environment variable instead of demonstrating the local loopback address.


### 2. Why is it important to use environment variables instead of hard-coding configurations in your application?

It is also portable and secure with the assistance of the environment variables. Hard-coding settings results in it being hard to transfer the app between the varying environments (development, staging, production) without altering the source code and recompiling. With environment variables we may be able to modify the database or broker settings profane. It as well avoids the commitment of sensitive credentials such as passwords of RabbitMQ to version control.

### 3. Why is it important to have separate repositories for each microservice? How does this help maintain independence and scalability?

Factor 1: Codebase is enforced in separate repositories, which require a 1-to-1 relationship between a repository and a service. This freedom enables teams to apply varying technology stacks (such as Rust to one service and Node.js to another) without versioning interactions. It is also independent in scaling and deployment
