# 🚀 Introduction to Spring Boot

**Spring Boot** is a framework built on top of the **Spring Framework** that simplifies the process of creating **production-ready** Java applications.  
It eliminates the need for complex XML configurations and makes it easy to build and run **standalone Spring applications** with minimal setup.

---

## 🌱 What Is Spring Boot?

Spring Boot is an **opinionated** framework — meaning it provides a set of defaults and conventions to help you get started quickly.  
It takes care of repetitive setup tasks like dependency management, configuration, and server setup so you can focus on writing business logic.

### 💡 In Short:
> Spring Boot = Spring + Auto Configuration + Embedded Server + Production Tools

---

## ⚙️ Why Use Spring Boot?

| Feature                  | Description                                                                                              |
|--------------------------|----------------------------------------------------------------------------------------------------------|
| **Auto Configuration**   | Automatically configures your application based on the libraries you include.                            |
| **Embedded Servers**     | Comes with built-in web servers (Tomcat, Jetty, Undertow) — no need for external deployment.             |
| **Starter Dependencies** | Provides pre-defined dependency groups like `spring-boot-starter-web` or `spring-boot-starter-data-jpa`. |
| **Production Ready**     | Includes metrics, health checks, and monitoring out of the box.                                          |
| **Simplified Setup**     | Create and run a project with minimal configuration.                                                     |

---

## 🧩 Creating a Spring Boot Project

You can quickly generate a Spring Boot project using the **[Spring Initializr](https://start.spring.io/)** — an online tool that helps you bootstrap a new project.

### ✅ Steps to Create a Project

1. Go to [start.spring.io](https://start.spring.io/)
2. Choose:
   - **Project:** Maven Project  
   - **Language:** Java  
   - **Spring Boot Version:** 3.x  
3. Add dependencies:
   - `Spring Web`
   - `Spring Boot DevTools`
   - (optional) `Spring Boot Test`
4. Fill project metadata:
   - Group: `com.example`
   - Artifact: `demo`
5. Click **Generate** → A `.zip` file will download.
6. Extract it and open in **IntelliJ IDEA** or **VS Code**.

---

## 🧱 Folder Structure

Once opened, you’ll see the following structure:

```
demo/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/example/demo/
│   │   │       ├── DemoApplication.java      → Main entry point
│   │   │       └── controller/               → REST controllers
│   │   │       └── service/                  → Business logic
│   │   │       └── repository/               → Data access layer
│   │   │       └── model/                    → Data classes or entities
│   │   └── resources/
│   │       └── application.properties        → Configuration file
│   └── test/java/                            → Unit tests
└── pom.xml                                   → Dependency management
```

---

## 🏃 Running Your Application

### Using IntelliJ IDEA:
- Open the project  
- Locate `DemoApplication.java`  
- Click **Run ▶️** — Spring Boot will start an embedded **Tomcat server**

### Using Command Line:
```bash
mvn spring-boot:run
```

Once the app starts, open your browser and visit:
```
http://localhost:8080
```

---

## 🧠 The `@SpringBootApplication` Annotation

Every Spring Boot application has a main class annotated with `@SpringBootApplication`.

Example:
```java
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class DemoApplication {
    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }
}
```

### It Combines Three Annotations:
- `@Configuration` – Marks the class as a source of bean definitions  
- `@EnableAutoConfiguration` – Enables automatic configuration  
- `@ComponentScan` – Scans the package for Spring components  

---

## 🧰 Common Starter Dependencies

| Starter                        | Purpose                                  |
|--------------------------------|------------------------------------------|
| `spring-boot-starter-web`      | Build web applications and REST APIs     |
| `spring-boot-starter-data-jpa` | Connect and interact with databases      |
| `spring-boot-starter-security` | Add authentication and authorization     |
| `spring-boot-starter-test`     | Support for unit and integration testing |
| `spring-boot-devtools`         | Auto-restart and faster development      |

---

## 💡 Example: Simple REST API

Once your project is running, you can create a quick REST endpoint:

```java
package com.example.demo.controller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {

    @GetMapping("/")
    public String hello() {
        return "Hello, Spring Boot!";
    }
}
```

Open your browser or Postman and visit:
```
http://localhost:8080/
```

You should see:
```
Hello, Spring Boot!
```

---

## 🎯 Summary

By now, you should understand:
- What Spring Boot is and why it’s widely used  
- How to create and run a Spring Boot project  
- The basic folder structure and key annotations  
- How to build your first REST endpoint  


