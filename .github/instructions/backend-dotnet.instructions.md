# Backend (.NET) Instructions

## Purpose

- Define backend development standards for all AI-generated .NET code.
- Support a lightweight Clean Architecture approach with clear responsibility boundaries.
- Ensure generated backend artifacts are maintainable, testable, and aligned with API-driven delivery.

## Target Technology Stack

- Framework
  - .NET 8 (LTS): chosen for long-term support, modern language features, and platform stability.
  - ASP.NET Core Web API: proven, high-performance framework for building HTTP APIs.

- Data Access
  - Entity Framework Core 8: idiomatic ORM for .NET, simplifies data access and migrations.
  - SQL Server: reliable, enterprise-grade relational database with strong tooling and support.

- Validation
  - FluentValidation: expressive, testable validation rules maintained separately from models.

- Object Mapping
  - AutoMapper: allow only when it meaningfully reduces boilerplate and improves maintainability.

- Logging
  - Serilog: structured, extensible logging with rich sinks and observability support.

- API Documentation
  - Swagger / OpenAPI: standardized API contract and interactive documentation.

- Testing
  - xUnit: primary test framework for unit and integration tests.
  - Moq: mocking library for isolating dependencies in unit tests.

AI agents should use the approved technology stack by default and must not introduce additional frameworks, libraries, or architectural patterns unless explicitly instructed to do so.

## Architecture Style

- Use a simplified Clean Architecture model with the following layers:
  - API Layer: Controllers or minimal APIs handle HTTP requests and responses.
  - Application Layer: Services or use cases implement business workflows and orchestrate operations.
  - Domain Layer: Entities and business rules encapsulate core domain behavior.
  - Infrastructure Layer: Data access, persistence, and external integrations.
- Domain layer owns business invariants.
- Application layer orchestrates workflows and coordinates services.
- No business logic belongs in controllers or the API layer.

## Project Structure Rules

- Keep layers separated by folder or project boundaries.
- Place controllers in the API layer.
- Place business orchestration and service interfaces in the Application layer.
- Place domain entities, value objects, and domain rules in the Domain layer.
- Place persistence, external API clients, and infrastructure implementations in the Infrastructure layer.
- Keep cross-layer dependencies flowing inward: API → Application → Domain; Infrastructure implements contracts.

## Service Design Rules

- Each service must represent a single use case or business capability.
- Avoid god services and multi-responsibility services.
- Keep orchestration in the Application layer only.
- Expose focused service methods that align with business intent.
- Prefer small service interfaces and clear use-case boundaries.

## API Design Standards

- Use RESTful, resource-oriented endpoints with clear naming.
- Prefer simple controllers or minimal APIs for CRUD and service operations.
- Always use DTOs for request and response payloads.
- Keep controllers thin and delegate business logic to the Application layer.
- Return appropriate HTTP status codes and consistent response shapes.

## API Design Enforcement Rules

- Use standard endpoint naming conventions: /resources, /resources/{id}, /resources/{id}/subresources.
- Version APIs via route prefix or header versioning, e.g. /api/v1/
- Use a consistent request/response structure with top-level metadata when required.
- Support pagination, filtering, and sorting with standardized query parameters.
- Use consistent HTTP status code rules: 200 for success, 201 for creation, 204 for no content, 400 for client errors, 401/403 for auth failures, 404 for missing resources, 409 for conflicts, 500 for server errors.

## Standard API Response Contract

- Return a unified response schema for all APIs.
- Include a success flag, data payload, and an error section when applicable.
- Use consistent field naming across responses.
- Ensure error responses include a code, message, and optional details.
- Keep success responses predictable and machine-readable.

Example error response:

```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "One or more validation rules failed",
    "details": [
      "Field 'amount' must be greater than zero.",
      "Field 'accountId' is required."
    ]
  }
}
```
Example success response:

```json
{
  "success": true,
  "data": {
    "accountId": 101,
    "balance": 2500
  },
  "error": null
}
```

## Dependency Injection Rules

- Use constructor injection for services and repository dependencies.
- Register abstractions in the DI container, not concrete implementations directly in consumers.
- Keep service lifetimes appropriate to workload: singleton for stateless services, scoped for request-bound components.
- Avoid service locators or manual dependency resolution in controllers.

## Data Access Rules

- Use EF Core or equivalent as the primary data access approach.
- Keep DbContext usage confined to the Infrastructure layer.
- Use repository or data access abstractions only when they simplify testing and encapsulate persistence concerns.
- Avoid spreading EF Core logic into the Application or API layers.
- Keep database access efficient and keep transactions explicit where needed.

## Transaction & Consistency Rules

- Use database transactions for multi-step workflows that must remain atomic.
- Ensure business-critical operations complete fully or roll back to prevent partial state updates.
- Keep transaction scope narrow and explicitly defined in the Infrastructure or Application layer.
- Avoid cross-request or long-running transactions unless required for consistency.

## Async Programming Rules

- Implement all I/O operations asynchronously.
- Avoid blocking calls such as .Result or .Wait.
- Use async/await consistently in Application and Infrastructure layers.
- Ensure asynchronous methods are propagated through the call chain.

## DTO and Mapping Rules

- Define separate DTOs for API requests and responses.
- Map between DTOs and domain models in the Application layer or dedicated mapping services.
- Avoid exposing domain entities directly through API contracts.
- Keep mapping simple and explicit; use mapping helpers or libraries only when they reduce boilerplate without obscuring intent.

## Error Handling Strategy

- Handle exceptions centrally using middleware or filters.
- Return structured error responses with meaningful messages and status codes.
- Do not expose internal runtime details or stack traces in API responses.
- Use domain-specific exceptions for business validation and translate them to client-friendly responses.

## Validation Rules

- Validate request data before invoking business logic.
- Keep validation rules close to the API boundary or Application layer.
- Use explicit validation logic; prefer model validation and service-level checks.
- Do not rely on controllers to implement business validation.
- Follow validation hierarchy: DTO validation for input format, Application validation for business rules, Domain validation for invariants.

## Logging Standards

- Log at appropriate levels: information for normal flow, warning for recoverable issues, error for failures.
- Avoid logging sensitive data such as credentials or personal data.
- Include contextual information to support diagnostics.
- Use structured logging patterns when available.
- Use a consistent structured log format with fields such as correlationId, timestamp, log level, service name, message, and metadata.
- Log meaningful business events in addition to technical failures.

## Security Guidelines

- Enforce authentication and authorization at the API boundary.
- Validate and sanitize external input.
- Avoid storing secrets in source code.
- Apply least privilege to backend operations and external integrations.
- Never expose internal exception messages, stack traces, connection strings, or sensitive implementation details to API consumers.

## Performance Guidelines

- Prefer simple, efficient implementations.
- Avoid unnecessary database queries and redundant processing.
- Keep payloads minimal and use paging for collections.
- Document performance assumptions when they influence design.

## Testing Expectations

- Generate code that supports unit and integration testing.
- Test controllers or APIs for request routing and response handling.
- Test Application layer services for business logic and orchestration.
- Test domain behavior independently of infrastructure.
- Keep tests focused, readable, and maintainable.
- Prefer deterministic tests that do not depend on external services or shared state.

## AI Behavior Rules

- Do not over-engineer services.
- Prefer minimal APIs or simple controllers when appropriate.
- Do not create unnecessary abstractions.
- Always use DTOs for API communication.
- Keep business logic out of controllers.
- Do not assume missing requirements; ask for clarification when behavior is unclear.

## Code Review Checklist

- Is the layer separation clear and consistent?
- Are controllers thin and API-focused?
- Are DTOs used for all API requests and responses?
- Is business logic confined to the Application or Domain layer?
- Is dependency injection used correctly and consistently?
- Are error handling and validation implemented at the right layer?
- Are security and logging concerns addressed appropriately?
- Is the code simple, maintainable, and not over-engineered?
