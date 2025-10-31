# 🌐 Building RESTful Endpoints with Spring Boot

Now that you understand **IoC** and **DI**, let’s use them to build **RESTful APIs** in a Spring Boot application.  
Spring Boot makes it incredibly simple to create endpoints that handle HTTP requests such as **GET**, **POST**, **PUT**, and **DELETE**.

---

## 🚀 What Is a RESTful API?

A **RESTful API** (Representational State Transfer) allows clients (like browsers or frontend apps) to communicate with your backend using standard HTTP methods.

| HTTP Method | Purpose       | Example           |
|-------------|---------------|-------------------|
| `GET`       | Retrieve data | Get all users     |
| `POST`      | Create data   | Add a new user    |
| `PUT`       | Update data   | Edit user details |
| `DELETE`    | Delete data   | Remove a user     |

---

## 🧱 Example Project: User Management API

### ✅ Project Structure
```
src/
 └── main/
     └── java/com/example/demo/
         ├── controller/
         │   └── UserController.java
         ├── model/
         │   └── User.java
         ├── service/
         │   └── UserService.java
         └── repository/
             └── UserRepository.java
```

We’ll create a simple API with endpoints to:
- List all users  
- Get a user by ID  
- Add a new user  
- Delete a user  

---

## 🧩 Step 1: The Model
```java
package com.example.demo.model;

public class User {
    private Long id;
    private String name;
    private String email;

    // Constructors
    public User() {}

    public User(Long id, String name, String email) {
        this.id = id;
        this.name = name;
        this.email = email;
    }

    // Getters and setters
    public Long getId() { return id; }
    public void setId(Long id) { this.id = id; }

    public String getName() { return name; }
    public void setName(String name) { this.name = name; }

    public String getEmail() { return email; }
    public void setEmail(String email) { this.email = email; }
}
```

---

## 🧠 Step 2: The Service
```java
package com.example.demo.service;

import com.example.demo.model.User;
import org.springframework.stereotype.Service;

import java.util.*;

@Service
public class UserService {

    private final Map<Long, User> users = new HashMap<>();

    public List<User> getAllUsers() {
        return new ArrayList<>(users.values());
    }

    public User getUserById(Long id) {
        return users.get(id);
    }

    public User addUser(User user) {
        users.put(user.getId(), user);
        return user;
    }

    public void deleteUser(Long id) {
        users.remove(id);
    }
}
```

---

## 🌍 Step 3: The Controller
```java
package com.example.demo.controller;

import com.example.demo.model.User;
import com.example.demo.service.UserService;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
@RequestMapping("/api/users")
public class UserController {

    private final UserService userService;

    // Constructor injection (IoC + DI)
    public UserController(UserService userService) {
        this.userService = userService;
    }

    // GET /api/users
    @GetMapping
    public List<User> getAllUsers() {
        return userService.getAllUsers();
    }

    // GET /api/users/{id}
    @GetMapping("/{id}")
    public User getUserById(@PathVariable Long id) {
        return userService.getUserById(id);
    }

    // POST /api/users
    @PostMapping
    public User addUser(@RequestBody User user) {
        return userService.addUser(user);
    }

    // DELETE /api/users/{id}
    @DeleteMapping("/{id}")
    public void deleteUser(@PathVariable Long id) {
        userService.deleteUser(id);
    }
}
```

---

## ⚡ Step 4: Test the API

Run the application (`DemoApplication.java`).

Then, use a tool like **Postman** or **curl** to test your endpoints:

### ▶️ Get All Users
```bash
GET http://localhost:8080/api/users
```

### ➕ Add a New User
```bash
POST http://localhost:8080/api/users
Content-Type: application/json

{
  "id": 1,
  "name": "Sam",
  "email": "sam@example.com"
}
```

### 🔍 Get User by ID
```bash
GET http://localhost:8080/api/users/1
```

### ❌ Delete a User
```bash
DELETE http://localhost:8080/api/users/1
```

---

## 💡 Notes

- `@RestController` combines `@Controller` and `@ResponseBody`, returning JSON by default.  
- `@RequestMapping("/api/users")` defines the base URL for this controller.  
- `@GetMapping`, `@PostMapping`, `@DeleteMapping` are shortcuts for specific HTTP methods.  
- The service layer ensures **separation of concerns** — business logic stays out of controllers.  

---

## 🧠 Summary

| Layer          | Responsibility                              |
|----------------|---------------------------------------------|
| **Controller** | Handles HTTP requests and responses         |
| **Service**    | Contains business logic                     |
| **Repository** | (Optional here) Handles database operations |
| **Model**      | Represents the data structure               |

---


