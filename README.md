# Week 8: Spring Boot Basics

This week introduces **Spring Boot**, a powerful framework that simplifies the development of production-ready Java applications.  
Students will learn how to create **RESTful APIs**, understand the **Spring architecture**, and build a well-structured backend using
controllers, services, and repositories.

---

## Topics Covered

### 1. What is Spring & Why Use It
- Overview of the **Spring Framework** and its core features  
- Introduction to **Spring Boot** and **autoconfiguration**  
- Benefits of using Spring Boot over plain Java projects  
- Understanding **Inversion of Control (IoC)** and **Dependency Injection (DI)**  

### 2. Setting Up a Spring Boot Project
- Using [Spring Initializer](https://start.spring.io/) to generate a new project  
- Adding key dependencies:
  - `spring-boot-starter-web` (for building REST APIs)
  - `spring-boot-devtools` (for auto-restart)
  - `spring-boot-starter-test` (for testing)
- Understanding the standard folder structure:

```txt
src/main/java        → application source code
src/main/resources   → configuration files (application.properties)
src/test/java        → test files
pom.xml              → project configuration
```
- Running a Spring Boot app using the **main class** and embedded Tomcat server

### 3. Building RESTful APIs
- What is a REST API and how HTTP verbs (GET, POST, PUT, DELETE) map to CRUD  
- Creating endpoints with:
  - `@RestController`  
  - `@RequestMapping`, `@GetMapping`, `@PostMapping`, `@DeleteMapping`  
- Returning JSON responses using Spring Boot’s built-in Jackson support  
- Testing endpoints with **Postman**

### 4. Controller–Service–Repository Structure
- Understanding layered architecture:

```txt
controller/   → handles HTTP requests
service/      → contains business logic
repository/   → data access layer (in-memory for now)
model/        → data classes or entities

```
- Using `@Service` and `@Autowired` for dependency injection  
- Writing simple CRUD logic with in-memory data (e.g., `ArrayList`)

---

## 🧰 Recommended Tools

| Tool                   | Purpose                                      |
|------------------------|----------------------------------------------|
| **IntelliJ IDEA**      | Develop and run Spring Boot projects         |
| **Spring Initializer** | Generate Spring Boot starter projects        |
| **Maven**              | Manage dependencies and build automation     |
| **Postman**            | Test REST API endpoints                      |
| **Java 17+**           | Required language version for Spring Boot 3+ |

---

## 🎯 Learning Outcomes

By the end of Week 8, students will be able to:
- Understand the purpose of the Spring and Spring Boot frameworks
- Create and configure a Spring Boot project from scratch
- Build and test simple RESTful APIs
- Use annotations such as `@RestController`, `@Service`, and `@Autowired`
- Apply layered architecture for clean and maintainable code
- Run a Spring Boot app locally using an embedded web server

---
