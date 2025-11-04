# 🚀 10 Spring Boot Project Ideas – Week 8

Week 8 focuses on learning **Spring Boot fundamentals**, **IoC/DI**, and **REST API creation**.  
These 10 projects are designed to be practical, engaging, and achievable within the week — without
yet introducing databases (use lists or maps for data storage).  

---

## Dependencies to Include:
```xml
<dependencies>
   <!-- Spring Web Starter -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <!-- Spring Boot Test Starter -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
    </dependency>

    <!-- Spring Boot DevTools -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-devtools</artifactId>
        <optional>true</optional>
    </dependency>
    
    <!-- Spring Data JPA -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>
    
    <!-- Bean Validation -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-validation</artifactId>
    </dependency>

    <!-- PostgreSQL driver -->
    <dependency>
        <groupId>org.postgresql</groupId>
        <artifactId>postgresql</artifactId>
        <scope>runtime</scope>
    </dependency>
</dependencies>
```

## 1. 👥 User Management API

**Goal:** Learn to build basic REST endpoints and manage data using in-memory collections.

**Description:**  
Create a REST API that allows adding, viewing, updating, and deleting users.  
Each user has an `id`, `name`, `email`, and `role`.

**Endpoints:**
```
GET /users               → Get all users
GET /users/{id}          → Get a user by ID
POST /users              → Create a new user
PUT /users/{id}          → Update an existing user
DELETE /users/{id}       → Delete a user
```

**Learning Focus:**  
- Using `@RestController`, `@Service`, and `@Autowired`  
- Working with `List<User>` for in-memory data  
- Returning `ResponseEntity` with proper status codes  

**Extension:**  
Add validation to ensure emails are unique and required.

---

## 2. 📚 Book Library API

**Goal:** Practice CRUD operations with structured data and request validation.

**Description:**  
Create a system to manage a small library of books.  
Each book includes: `id`, `title`, `author`, `year`, `genre`.

**Endpoints:**
```
GET /books                   → List all books
GET /books/{id}              → Get book details
POST /books                  → Add a new book
PUT /books/{id}              → Edit an existing book
DELETE /books/{id}           → Remove a book
GET /books/search?author=X   → Find books by author
```

**Learning Focus:**  
- Handling query parameters with `@RequestParam`  
- Using `@PathVariable` for dynamic URLs  
- Creating reusable service and repository layers  

**Extension:**  
Add filtering by `genre` and sorting by year.

---

## 3. 📝 TODO List API

**Goal:** Learn how to manage application state and update resource attributes.

**Description:**  
Build a task manager that allows users to create, update, mark as done, and delete tasks.

Each task has: `id`, `title`, `description`, `status` (`pending`, `done`).

**Endpoints:**
```
GET /tasks              → View all tasks
GET /tasks/{id}         → Get one task
POST /tasks             → Add a new task
PATCH /tasks/{id}/done  → Mark task as done
DELETE /tasks/{id}      → Delete a task
```

**Learning Focus:**  
- Using different HTTP methods (`PATCH`, `DELETE`)  
- Applying DTOs for requests/responses  
- Practicing data filtering in services  

**Extension:**  
Add support for task due dates and priority levels.

---

## 4. 🎬 Movie Review API

**Goal:** Practice relationships between entities (movie → reviews) and nested endpoints.

**Description:**  
Users can add movies and submit reviews for them.  
Each movie has a list of reviews stored in-memory.

**Endpoints:**
```
GET /movies                      → Get all movies
POST /movies                     → Add a new movie
GET /movies/{id}/reviews         → Get reviews for one movie
POST /movies/{id}/reviews        → Add a new review
DELETE /movies/{id}/reviews/{r}  → Delete a review
```

**Learning Focus:**  
- Modeling one-to-many relationships  
- Using nested routes and `@PathVariable`  
- Handling lists of objects inside objects  

**Extension:**  
Add rating averages and top-rated movie endpoints.

---

## 5. 🍔 Restaurant Menu API

**Goal:** Understand hierarchical data and nested resources.

**Description:**  
Build a system for managing restaurants and their menus.  
Each restaurant has a name, address, and list of menu items.

**Endpoints:**
```
GET /restaurants                 → All restaurants
POST /restaurants                → Add a restaurant
GET /restaurants/{id}/menu       → List menu items
POST /restaurants/{id}/menu      → Add menu item
DELETE /restaurants/{id}/menu/{itemId} → Delete item
```

**Learning Focus:**  
- Nested data structures  
- CRUD inside nested collections  
- Designing clear, intuitive REST paths  

**Extension:**  
Add prices, categories, and endpoints for daily specials.

---

## 6. 🛍️ Product Catalog API

**Goal:** Practice pagination, filtering, and sorting.

**Description:**  
Develop an API for browsing products in a catalog.  
Each product includes: `id`, `name`, `category`, `price`, `stock`.

**Endpoints:**
```
GET /products?page=1&limit=10        → Paginated products
GET /products?category=clothes       → Filter by category
POST /products                       → Add product
PUT /products/{id}                   → Update product
DELETE /products/{id}                → Delete product
```

**Learning Focus:**  
- Handling query parameters  
- Implementing pagination manually with `List.subList()`  
- Sorting data in service layer  

**Extension:**  
Add search by keyword or price range.

---

## 7. 🎵 Music Playlist Service

**Goal:** Apply object composition and nested resource management.

**Description:**  
Each user can create playlists containing multiple songs.

**Endpoints:**
```
POST /users/{id}/playlists                → Create playlist
GET /users/{id}/playlists                 → List all playlists
POST /users/{id}/playlists/{pid}/songs    → Add song
DELETE /users/{id}/playlists/{pid}/songs/{sid} → Remove song
```

**Learning Focus:**  
- Managing multiple nested entities  
- Working with `List<List<Song>>` data structures  
- Reusing services for related entities  

**Extension:**  
Add song duration, total playlist time, and favorite playlists.

---

## 8. 🚗 Car Rental API

**Goal:** Learn about domain-driven API design and basic validation.

**Description:**  
Create an API to manage cars, customers, and rentals.  
Each rental includes the car, customer, start date, and end date.

**Endpoints:**
```
GET /cars                     → List cars
POST /cars                    → Add car
POST /customers               → Register customer
POST /rentals                 → Create new rental
GET /rentals/{id}             → View rental details
```

**Learning Focus:**  
- Multiple entities in one project  
- Validating date ranges (start < end)  
- Designing resource-oriented endpoints  

**Extension:**  
Prevent overlapping rentals for the same car.

---

## 9. 🌦️ Weather Tracker

**Goal:** Learn how to consume external APIs with `RestTemplate`.

**Description:**  
Use an open weather API to fetch and display weather data for a given city.

**Endpoints:**
```
GET /weather/{city}          → Returns temperature, humidity, and description
```

**Learning Focus:**  
- Using `RestTemplate` or `WebClient`  
- Consuming JSON APIs  
- Returning structured JSON responses  

**Extension:**  
Cache results in memory (Map<City, WeatherResponse>) for faster access.

---

## 10. 📰 News Aggregator

**Goal:** Combine API consumption and filtering in your own endpoints.

**Description:**  
Fetch and expose the latest news articles from a public API (e.g., NewsAPI).  
Filter by category, keyword, or country.

**Endpoints:**
```
GET /news                    → All top headlines
GET /news?category=business  → Filtered by category
GET /news/search?query=java  → Search for articles
```

**Learning Focus:**  
- Using `RestTemplate`  
- Handling external JSON  
- Creating a simplified response model  

**Extension:**  
Allow users to mark favorite articles in memory.

---



