# Sample cURL commands

Start the API first with `mvn spring-boot:run`. Base URL: `http://localhost:8080`.

## Create employee — 201 Created
```bash
curl -i -X POST http://localhost:8080/api/employees \
  -H "Content-Type: application/json" \
  -d '{"name":"Ananya Rao","email":"ananya.rao@example.com","department":"Engineering"}'
```

## List employees — 200 OK
```bash
curl -i http://localhost:8080/api/employees
```

## Get employee by ID — 200 OK (or 404 Not Found)
```bash
curl -i http://localhost:8080/api/employees/1
```

## Update employee — 200 OK
```bash
curl -i -X PUT http://localhost:8080/api/employees/1 \
  -H "Content-Type: application/json" \
  -d '{"name":"Ananya Rao","email":"ananya.rao@example.com","department":"Platform"}'
```

## Delete employee — 204 No Content (or 404 Not Found)
```bash
curl -i -X DELETE http://localhost:8080/api/employees/1
```

## Validation error — 400 Bad Request
```bash
curl -i -X POST http://localhost:8080/api/employees \
  -H "Content-Type: application/json" \
  -d '{"name":"","email":"not-an-email","department":""}'
```

## Duplicate email — 409 Conflict
Create an employee, then try creating another employee using the same email.
