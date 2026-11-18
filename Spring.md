
# Top 30 Spring Boot Interview Questions and Answers for Freshers

## 1. Spring Framework and Spring Boot Basics

### 1. What is Spring Framework?

Spring Framework is an open-source Java framework used to develop enterprise applications.

It simplifies Java application development by providing features like:

- Dependency Injection (DI).
- Inversion of Control (IoC).
- Aspect-Oriented Programming (AOP).
- Transaction Management.
- Database Integration.
- Web Application Development.

**Example:** Spring helps us manage objects and their dependencies instead of creating and managing everything manually.

### 2. What is Spring Boot?

Spring Boot is an extension of the Spring Framework that makes it easier to develop standalone, production-ready Spring applications.

It reduces configuration and provides features like:

- Auto Configuration.
- Starter Dependencies.
- Embedded Servers.
- Production-ready features through Actuator.

**Example:** We can create a Spring Boot application and run it directly without deploying it separately on an external Tomcat server.

### 3. Difference between Spring and Spring Boot?

Spring is a framework used to develop Java applications, whereas Spring Boot simplifies Spring application development by reducing manual configuration.

| Spring Framework | Spring Boot |
|---|---|
| Requires more configuration. | Requires less configuration. |
| Server configuration may be manual. | Provides embedded servers. |
| Dependency management is more manual. | Provides starter dependencies. |
| No automatic configuration by default. | Provides auto-configuration. |
| More setup is required. | Faster application development. |

### 4. What are the advantages of Spring Boot?

The main advantages of Spring Boot are:

1. **Auto Configuration:** Automatically configures components based on dependencies and application settings.
2. **Embedded Server:** Provides servers like Tomcat.
3. **Starter Dependencies:** Simplifies dependency management.
4. **Less Configuration:** Reduces XML and manual configuration.
5. **Production Ready:** Provides monitoring and health-checking features using Actuator.
6. **Easy Development:** Helps developers build applications quickly.

---

## 2. Spring Core Concepts

### 5. What is Dependency Injection?

Dependency Injection is a design pattern in which Spring provides the required objects (dependencies) to a class instead of the class creating those objects itself.

**Example:**

```java
@Service
public class UserService {

    private final UserRepository userRepository;

    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
}
```

Here, Spring injects the `UserRepository` object into `UserService`.

**Interview tip:** Dependency Injection helps achieve loose coupling and makes applications easier to test and maintain.

### 6. What is Inversion of Control (IoC)?

Inversion of Control is a design principle in which the control of creating, managing, and injecting objects is given to the Spring IoC container instead of the developer managing everything manually.

**Example:**

Normally, we create objects using:

```java
UserService userService = new UserService();
```

In Spring, the IoC container manages object creation and dependency injection.

**Remember:**
- IoC is a design principle.
- DI is one way to implement IoC.
- Spring IoC container manages Spring Beans.

### 7. What is a Spring Bean?

A Spring Bean is an object that is created, configured, and managed by the Spring IoC container.

We can create Spring Beans using annotations like:

- `@Component`
- `@Service`
- `@Repository`
- `@Controller`

We can also define beans using the `@Bean` annotation inside a configuration class.

### 8. What is the purpose of `@SpringBootApplication`?

`@SpringBootApplication` is the main annotation used to start a Spring Boot application.

It combines three important annotations:

1. `@SpringBootConfiguration` – Indicates that the class provides Spring configuration.
2. `@EnableAutoConfiguration` – Enables Spring Boot's auto-configuration.
3. `@ComponentScan` – Scans components in the package and its subpackages.

**Example:**

```java
@SpringBootApplication
public class MyApplication {

    public static void main(String[] args) {
        SpringApplication.run(MyApplication.class, args);
    }
}
```

### 9. Difference between `@Component`, `@Service` and `@Repository`?

All three annotations are used to define Spring-managed beans, but they represent different responsibilities.

| Annotation | Purpose |
|---|---|
| `@Component` | General-purpose Spring Bean. |
| `@Service` | Used for business logic. |
| `@Repository` | Used for database operations. |

**Example:**

```java
@Component
public class MyComponent {
}
```

```java
@Service
public class UserService {
}
```

```java
@Repository
public class UserRepository {
}
```

**Interview tip:** `@Service` and `@Repository` are specialized forms of `@Component`. `@Repository` also supports persistence exception translation.

### 10. What is `@Autowired`?

`@Autowired` is an annotation used to inject dependencies automatically by Spring.

It can be used for constructor, setter, and field injection.

**Example:**

```java
@Service
public class UserService {

    private final UserRepository repository;

    @Autowired
    public UserService(UserRepository repository) {
        this.repository = repository;
    }
}
```

**Interview tip:** Constructor injection is generally recommended because it makes dependencies explicit and supports immutable fields. With a single constructor, `@Autowired` is optional.

---

## 3. Spring MVC and REST API

### 11. What is `@RestController`?

`@RestController` is an annotation used to create RESTful web services in Spring Boot.

It combines two annotations:

- `@Controller`
- `@ResponseBody`

It returns data directly as JSON or other response formats instead of returning a view name.

**Example:**

```java
@RestController
public class UserController {

    @GetMapping("/users")
    public String getUsers() {
        return "Hello Users";
    }
}
```

### 12. Difference between `@Controller` and `@RestController`?

| @Controller | @RestController |
|---|---|
| Used mainly for MVC applications. | Used mainly for REST APIs. |
| Usually returns view names. | Returns response data directly. |
| Requires `@ResponseBody` to return data directly. | Includes `@ResponseBody` automatically. |
| Used with view technologies like Thymeleaf. | Commonly used with JSON responses. |

### 13. What is `@RequestMapping`?

`@RequestMapping` is an annotation used to map HTTP requests to controller classes or methods.

It can define:

- URL path.
- HTTP method.
- Request parameters.
- Headers.
- Content types.

**Example:**

```java
@RestController
@RequestMapping("/api/users")
public class UserController {

    @RequestMapping(value = "/all",
                    method = RequestMethod.GET)
    public String getUsers() {
        return "All Users";
    }
}
```

Here, the endpoint is `/api/users/all`.

### 14. Difference between `@GetMapping`, `@PostMapping`, `@PutMapping` and `@DeleteMapping`?

These annotations are used to handle different HTTP methods.

| Annotation | Purpose | Example |
|---|---|---|
| `@GetMapping` | Retrieve data. | Get user |
| `@PostMapping` | Create new data. | Add user |
| `@PutMapping` | Update or replace data. | Update user |
| `@DeleteMapping` | Delete data. | Delete user |

**Example:**

```java
@GetMapping("/users")
public List<User> getUsers() {
    return userService.getAllUsers();
}

@PostMapping("/users")
public User addUser(@RequestBody User user) {
    return userService.saveUser(user);
}

@PutMapping("/users/{id}")
public User updateUser(@PathVariable Long id,
                       @RequestBody User user) {
    return userService.updateUser(id, user);
}

@DeleteMapping("/users/{id}")
public void deleteUser(@PathVariable Long id) {
    userService.deleteUser(id);
}
```

### 15. What is a REST API?

REST stands for Representational State Transfer.

A REST API is an architectural style used for communication between applications over HTTP.

It allows clients like React applications to communicate with backend applications like Spring Boot.

**Example:**

A React application sends a GET request to:

```text
http://localhost:8080/api/users
```

The Spring Boot application processes the request and returns user data in JSON format.

### 16. What are HTTP methods?

HTTP methods define the type of operation that a client wants to perform on a server.

Important HTTP methods are:

| Method | Purpose |
|---|---|
| GET | Retrieve data. |
| POST | Create data. |
| PUT | Replace or update a resource. |
| PATCH | Partially update a resource. |
| DELETE | Delete a resource. |
| HEAD | Retrieve headers without the response body. |
| OPTIONS | Check supported communication options. |

### 17. What are HTTP status codes?

HTTP status codes indicate the result of an HTTP request.

They are divided into five categories.

| Status Code | Meaning |
|---|---|
| 200 OK | Request successful. |
| 201 Created | Resource successfully created. |
| 204 No Content | Successful request with no response body. |
| 400 Bad Request | Invalid request. |
| 401 Unauthorized | Authentication is required or has failed. |
| 403 Forbidden | Access is not allowed. |
| 404 Not Found | Resource not found. |
| 500 Internal Server Error | Server-side error. |
| 503 Service Unavailable | Server temporarily unavailable. |

**Interview tip:** Remember 200, 201, 400, 401, 403, 404 and 500.

---

## 4. Spring Data JPA and Hibernate

### 18. What is Spring Data JPA?

Spring Data JPA is a Spring module that simplifies database operations using the JPA specification.

It reduces boilerplate code by providing repository interfaces.

**Example:**

```java
public interface UserRepository
        extends JpaRepository<User, Long> {
}
```

We can perform operations like:

- Save records.
- Find records.
- Update records.
- Delete records.

We don't need to write SQL queries for common CRUD operations.

### 19. What is Hibernate?

Hibernate is an ORM (Object Relational Mapping) framework used in Java applications to interact with relational databases.

It maps Java objects to database tables and Java fields to table columns.

**Example:**

A Java `User` class can be mapped to a database `users` table.

Hibernate reduces the need to write SQL queries manually for common database operations.

### 20. Difference between JPA and Hibernate?

JPA is a specification, whereas Hibernate is an implementation of that specification.

| JPA | Hibernate |
|---|---|
| Jakarta Persistence specification. | ORM framework. |
| Defines standards and interfaces. | Provides implementation. |
| Cannot work independently without an implementation. | Can implement JPA and also provide additional features. |
| Defines annotations like `@Entity` and `@Id`. | Implements their functionality. |

**Interview tip:** Spring Data JPA provides repository abstractions, while Hibernate is commonly used as the JPA implementation.

### 21. What is an Entity?

An Entity is a Java class that represents a table in a relational database.

We use the `@Entity` annotation to mark a class as an entity.

**Example:**

```java
@Entity
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    private String email;
}
```

Here, the `User` class represents a database table.

### 22. What is `@Id`?

`@Id` is an annotation used to specify the primary key of an entity.

A primary key uniquely identifies each record in a database table.

**Example:**

```java
@Id
private Long id;
```

Here, `id` is the primary key of the User table.

### 23. What is `@GeneratedValue`?

`@GeneratedValue` is an annotation used to automatically generate primary key values for an entity.

Common generation strategies are:

1. `GenerationType.AUTO` – Provider chooses the strategy.
2. `GenerationType.IDENTITY` – Uses database identity or auto-increment columns.
3. `GenerationType.SEQUENCE` – Uses database sequences.
4. `GenerationType.TABLE` – Uses a database table to generate identifiers.

**Example:**

```java
@Id
@GeneratedValue(strategy = GenerationType.IDENTITY)
private Long id;
```

Here, the database automatically generates the ID.

### 24. Difference between `CrudRepository` and `JpaRepository`?

Both are Spring Data repository interfaces used to perform database operations.

| CrudRepository | JpaRepository |
|---|---|
| Provides basic CRUD operations. | Provides CRUD and additional JPA operations. |
| Supports save, find, delete, etc. | Supports CRUD, pagination, sorting, flushing and batch-related operations. |
| Has fewer features. | Has more features. |
| Suitable for basic CRUD requirements. | Suitable for JPA-based applications requiring additional features. |

**Interview tip:** `JpaRepository` extends `ListCrudRepository` and `ListPagingAndSortingRepository` in modern Spring Data versions, which provide list-oriented CRUD operations and paging/sorting functionality.

---

## 5. DTO and Exception Handling

### 25. What is DTO?

DTO stands for Data Transfer Object.

It is an object used to transfer data between different layers of an application or between client and server.

DTOs help us transfer only the required data instead of exposing the complete entity.

**Example:**

```java
public class UserDTO {

    private String name;
    private String email;

    // Getters and setters
}
```

### 26. Why do we use DTOs?

We use DTOs for the following reasons:

1. **Security:** Avoid exposing sensitive entity fields.
2. **Data Control:** Send only required fields to the client.
3. **Loose Coupling:** Separate API structure from database structure.
4. **Validation:** Apply validation rules to request data.
5. **Maintainability:** Changes to database entities don't necessarily affect API responses.

**Example:**

Suppose our User entity contains:

- ID
- Name
- Email
- Password

But the frontend only needs Name and Email.

We can use UserDTO to send only those two fields.

### 27. What is Global Exception Handling?

Global Exception Handling is a mechanism used to handle exceptions across the entire Spring Boot application from a centralized location.

We commonly use:

- `@ControllerAdvice`
- `@ExceptionHandler`

**Example:**

```java
@RestControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(RuntimeException.class)
    public ResponseEntity<String> handleException(
            RuntimeException ex) {

        return ResponseEntity
                .status(HttpStatus.INTERNAL_SERVER_ERROR)
                .body(ex.getMessage());
    }
}
```

**Advantages:**

- Centralized exception handling.
- Cleaner controller code.
- Consistent error responses.
- Better maintainability.

### 28. What is `@Valid`?

`@Valid` is an annotation used to trigger validation on an object based on the validation constraints defined on its fields.

It is commonly used to validate incoming request data.

**Example:**

```java
public class UserDTO {

    @NotBlank
    private String name;

    @Email
    private String email;

    @NotNull
    private Integer age;
}
```

In the controller:

```java
@PostMapping("/users")
public String addUser(@Valid @RequestBody UserDTO user) {
    return "User Added";
}
```

If the validation fails, Spring raises a validation exception that can be handled globally.

---

## 6. Spring Security and JWT

### 29. What is Spring Security?

Spring Security is a framework used to secure Java and Spring Boot applications.

It provides authentication and authorization.

**Authentication:** Checks who the user is.

**Authorization:** Checks what the user is allowed to access.

**Example:**

Suppose we have an application with two roles:

- ADMIN – Can add, update and delete users.
- USER – Can only view users.

Spring Security helps implement these access restrictions.

### 30. What is JWT Authentication?

JWT stands for JSON Web Token.

JWT is a compact token format commonly used to implement authentication in REST APIs.

After successful login, the server generates a JWT and sends it to the client.

The client stores the token and sends it with subsequent requests using the Authorization header.

```text
Authorization: Bearer <JWT_TOKEN>
```

The server validates the token before allowing access to protected resources.

**JWT contains three parts:**

1. Header – Contains token type and signing algorithm.
2. Payload – Contains claims such as user ID and roles.
3. Signature – Used to verify token integrity and authenticity.

**JWT Authentication Flow:**

1. User enters username and password.
2. Spring Boot backend validates user credentials.
3. Server generates and signs a JWT.
4. Client receives and stores the token securely.
5. Client sends JWT with subsequent requests.
6. Server validates JWT and grants access if valid and authorized.

**Important interview point:** JWT payload is encoded, not encrypted by default. Never store passwords or other sensitive information in its payload.

---

# Important Spring Boot Annotations – Quick Revision

| Annotation | Purpose |
|---|---|
| `@SpringBootApplication` | Main Spring Boot application. |
| `@Component` | Creates a Spring Bean. |
| `@Service` | Defines service layer. |
| `@Repository` | Defines repository layer. |
| `@Autowired` | Injects dependencies. |
| `@RestController` | Creates REST controllers. |
| `@Controller` | Creates MVC controllers. |
| `@RequestMapping` | Maps HTTP requests. |
| `@GetMapping` | Handles GET requests. |
| `@PostMapping` | Handles POST requests. |
| `@PutMapping` | Handles PUT requests. |
| `@DeleteMapping` | Handles DELETE requests. |
| `@RequestBody` | Reads request body. |
| `@PathVariable` | Reads URL path variables. |
| `@RequestParam` | Reads query parameters. |
| `@Entity` | Defines database entity. |
| `@Id` | Defines primary key. |
| `@GeneratedValue` | Generates primary key. |
| `@Valid` | Triggers validation. |
| `@ExceptionHandler` | Handles exceptions. |
| `@ControllerAdvice` | Global exception handling. |
| `@Transactional` | Manages transactions. |

---

# Practical Spring Boot Interview Questions

Prepare these practical questions as well:

1. Explain your Spring Boot project architecture.
2. Explain Controller, Service and Repository layers.
3. How does React communicate with Spring Boot?
4. How do you connect Spring Boot with MySQL?
5. Explain CRUD operations with an example.
6. How do you handle exceptions in your project?
7. How does JWT authentication work in your project?
8. What is the difference between `@PathVariable` and `@RequestParam`?
9. What is the difference between `PUT` and `PATCH`?
10. What happens when a Spring Boot application starts?

---

# Interview Preparation Tips for Freshers

1. Understand the concepts instead of memorizing answers.
2. Practice writing basic Spring Boot programs.
3. Learn CRUD operations using Spring Data JPA.
4. Understand how React communicates with Spring Boot.
5. Practice explaining your project architecture.
6. Be ready to explain every feature you implemented.
7. Learn basic SQL queries.
8. Practice explaining Dependency Injection and REST APIs with examples.

**Most important:** Interviewers often ask you to explain the Spring Boot project mentioned in your resume. Be ready to explain every feature you implemented, why you used it, and how the frontend communicates with the backend.
