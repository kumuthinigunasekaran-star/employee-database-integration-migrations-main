# Employee CRUD REST API

A starter CRUD REST API built with Spring Boot, Spring Web, Spring Data JPA, Bean Validation, and an in-memory H2 database.

## Requirements
- Java 21+
- Maven 3.9+ (or use your IDE's Maven support)

## Run locally
```bash
mvn spring-boot:run
```
The API runs at `http://localhost:8080`. The H2 database is in-memory and resets when the app stops.

## Endpoints

| Method | Endpoint | Success status | Purpose |
|---|---|---:|---|
| POST | `/api/employees` | 201 Created | Create an employee; includes `Location` header |
| GET | `/api/employees` | 200 OK | List employees |
| GET | `/api/employees/{id}` | 200 OK | Fetch one employee |
| PUT | `/api/employees/{id}` | 200 OK | Replace employee fields |
| DELETE | `/api/employees/{id}` | 204 No Content | Delete an employee |

Error handling:
- `400 Bad Request`: request validation fails
- `404 Not Found`: requested employee ID does not exist
- `409 Conflict`: email already belongs to another employee

## Example JSON
```json
{
  "name": "Ananya Rao",
  "email": "ananya.rao@example.com",
  "department": "Engineering"
}
```

## Design
- **Entity:** `Employee` is the JPA persistence model.
- **Request DTO:** `EmployeeRequest` defines accepted input and validation rules.
- **Response DTO:** `EmployeeResponse` controls the fields returned by the API.
- **Repository:** `EmployeeRepository` uses Spring Data JPA.
- **Service:** `EmployeeService` contains business logic.
- **Controller:** `EmployeeController` maps HTTP requests to service methods.
- **Exception handler:** `GlobalExceptionHandler` returns consistent HTTP errors.

## Try the API
See [`curl-examples.md`](curl-examples.md) for create, read, update, delete, and error examples.

## H2 console
While the app is running, visit `http://localhost:8080/h2-console`.
Use JDBC URL `jdbc:h2:mem:employeedb`, username `sa`, and leave password blank.

## Publish to GitHub
1. Create a new empty repository on GitHub named `employee-crud-api`.
2. Extract this project ZIP and open a terminal in the extracted folder.
3. Run:
   ```bash
   git init
   git add .
   git commit -m "Build employee CRUD REST API"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/employee-crud-api.git
   git push -u origin main
   ```
4. Replace `YOUR_USERNAME` with your GitHub username. Do not commit passwords, tokens, or other secrets.
