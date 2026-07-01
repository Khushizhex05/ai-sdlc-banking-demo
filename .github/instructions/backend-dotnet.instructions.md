# Backend (.NET) Instructions

## Purpose

Define the backend development standards for AI-generated .NET code.

The Backend Agent must use these guidelines together with the Solution Design document to generate clean, maintainable, and production-ready backend code.

---

# Inputs

The Backend Agent receives:

- Business Analysis document
- Solution Design document
- Backend Instructions

The Solution Design document is the primary source of truth.

If any conflict exists:

Solution Design > Business Analysis

Do not invent APIs, business rules, or workflows that are not present in the inputs.

---
# Tech Stack

- .NET 8
- ASP.NET Core Web API
- Entity Framework Core
- SQL Server
- FluentValidation
- AutoMapper (only when beneficial)
- Serilog
- Swagger / OpenAPI
- xUnit
- Moq

---

# Architecture

Follow a simplified Clean Architecture.

```
API
    ↓
Application
    ↓
Domain
    ↓
Infrastructure
```

Responsibilities:

### API

- Controllers
- Request validation
- HTTP responses
- No business logic

### Application

- Business logic
- Service interfaces
- DTO mapping
- Workflow orchestration

### Domain

- Entities
- Business rules
- Domain models

### Infrastructure

- EF Core
- Repositories
- External APIs
- Database access

Business logic must never be implemented inside Controllers.

---

# Project Structure

```
src/

API
│
├── Controllers
├── Middleware
├── Extensions

Application
│
├── Interfaces
├── Services
├── DTOs
│     ├── Requests
│     └── Responses
├── Validators
├── Mappers

Domain
│
├── Entities
├── Enums
├── Constants

Infrastructure
│
├── Persistence
├── Repositories
├── Configurations
```

Place new files in the appropriate layer.

---

# API Standards

Use REST conventions.

Examples

```
POST   /api/auth/login

GET    /api/accounts/{id}

POST   /api/transfers

PUT    /api/profile

DELETE /api/payees/{id}
```

Use appropriate HTTP status codes.

| Status | Purpose |
|---------|----------|
|200|Success|
|201|Created|
|204|No Content|
|400|Validation Error|
|401|Unauthorized|
|403|Forbidden|
|404|Not Found|
|409|Conflict|
|500|Server Error|

---

# API Response Format

Success

```json
{
  "success": true,
  "data": {}
}
```

Failure

```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Validation failed"
  }
}
```

Use this structure consistently.

---

# DTO Rules

- Always use Request DTOs.
- Always use Response DTOs.
- Never expose Entity classes directly.
- Keep DTOs focused on API contracts.

Example

```
LoginRequest

LoginResponse

TransferRequest

TransferResponse
```

---

# Validation

Use FluentValidation.

Example

```csharp
public class LoginRequestValidator
    : AbstractValidator<LoginRequest>
{
    public LoginRequestValidator()
    {
        RuleFor(x => x.Email)
            .NotEmpty()
            .EmailAddress();

        RuleFor(x => x.Password)
            .NotEmpty();
    }
}
```

Validation should happen before business logic execution.

---

# Dependency Injection

Use constructor injection only.

Example

```csharp
public class AuthService : IAuthService
{
    private readonly IUserRepository _repository;

    public AuthService(IUserRepository repository)
    {
        _repository = repository;
    }
}
```

Never use service locator patterns.

---

# Error Handling

Use centralized exception handling.

Example

```csharp
public class ExceptionMiddleware
{
}
```

Return consistent API responses.

Never expose:

- Stack traces
- Database errors
- Connection strings
- Internal implementation details

---

# Logging

Use Serilog.

Log:

- API requests
- Business events
- Exceptions
- Warnings

Do NOT log:

- Passwords
- Tokens
- Secrets
- Sensitive customer information

---

# Async Programming

Use async/await for all I/O operations.

Good

```csharp
await repository.SaveAsync(entity);
```

Avoid

```csharp
.Result

.Wait()
```

---

# Security

- Validate all incoming requests.
- Sanitize user input.
- Use HTTPS.
- Never hardcode secrets.
- Follow least-privilege principles.
- Return generic authentication errors where appropriate.

---

# Testing

Generate unit tests using:

- xUnit
- Moq

Generate tests for:

- Controllers
- Services
- Validators

Follow the Arrange → Act → Assert pattern.

Example

```csharp
[Fact]
public async Task Login_Should_Return_Success_When_Request_Is_Valid()
{
    // Arrange

    // Act

    // Assert
}
```

Cover:

- Successful execution
- Validation failures
- Business rule failures
- Exception scenarios

---

# Sample Implementation

## Controller

```csharp
[ApiController]
[Route("api/auth")]
public class AuthController : ControllerBase
{
    private readonly IAuthService _service;

    public AuthController(IAuthService service)
    {
        _service = service;
    }

    [HttpPost("login")]
    public async Task<IActionResult> Login(LoginRequest request)
    {
        var response = await _service.LoginAsync(request);

        return Ok(response);
    }
}
```

---

## Service

```csharp
public class AuthService : IAuthService
{
    private readonly IUserRepository _repository;

    public AuthService(IUserRepository repository)
    {
        _repository = repository;
    }

    public async Task<LoginResponse> LoginAsync(LoginRequest request)
    {
        // Business logic

        return new LoginResponse();
    }
}
```

---

## Repository

```csharp
public interface IUserRepository
{
    Task<User?> GetByEmailAsync(string email);
}
```

---

# AI Behavior Rules

Always

- Follow Clean Architecture.
- Keep Controllers thin.
- Place business logic in Services.
- Use DTOs.
- Use FluentValidation.
- Use async/await.
- Generate unit tests.
- Follow the Solution Design document.

Never

- Put business logic inside Controllers.
- Expose Entity models through APIs.
- Duplicate business logic.
- Hardcode configuration values.
- Invent APIs not described in the Solution Design.
- Assume missing requirements; leave them for clarification.

---

# Quality Checklist

Before completing generation, verify:

- Layering is correct.
- Controllers contain no business logic.
- DTOs are used.
- Validation is implemented.
- Exception handling is centralized.
- Logging is included where appropriate.
- Async methods are used.
- Tests are generated.
- Code follows .NET naming conventions.
- Output matches the Solution Design.