# SDLC: Software Development Life Cycle
<img width="627" height="627" alt="image" src="https://github.com/user-attachments/assets/31dc8e0a-6ef6-4e88-be84-28325ba5c66d" />

# Dependency: 
**an external component, such as a library, framework, or package, that an application requires to function properly**. It enables developers to reuse pre-written, tested code rather than building everything from scratch, which enhances efficiency but requires management to prevent security risks.

# Architecture
## Monolithic Architecture: 
A monolithic architecture is a traditional **software development model where all functional components of an application**, such as the user interface, business logic, and data access are **tightly coupled, built, and deployed together as a single, unified codebase.** 

## Microservice Architecture: 
A microservice architecture is a **software development model's design approach that structures an application as a collection of small, loosely coupled, and independently deployable services** organized around specific business capabilities. 

## Communication between microservices:
- **Synchronous Connection**: From one service, Request goes to API endpoint.
- **Asynchronous Connection**: **Middleware Between Microservices** (Message Broker) (**e.g., RabitMQ,Apache Kafka**) It uses it's brain and serves the request to dedicated service.

## Usage: 
Microservice architecture-**Large Application**, Monolithic Architecture-**Small projects**


Technologies like WebSockets allow bidirectional communication between client and server,  enabling instant updates. 
APIs: 

JWT tokens (stateless auth)
OAuth access tokens
Single-page apps with API auth

<img width="689" height="368" alt="image" src="https://github.com/user-attachments/assets/52196440-e7a2-4720-9557-b31b717ea1b0" />

Value Types:
String
Number
Boolean
Null
Object
Array (Collection of objects)
Each value pair ended with } creates a separate object.
