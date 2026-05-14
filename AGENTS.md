# AGENTS.md
## Purpose

This repository contains a Spring Boot full-stack web application for managing board games and reviews with role-based authentication and authorization.

This document helps AI agents and contributors understand repository structure, development workflow, and implementation conventions.

---

## Repository Structure

```text
src/
 ├── controllers/     # HTTP request handling
 ├── services/        # Business logic
 ├── repositories/   # Database access layer
 ├── templates/      # Thymeleaf templates
 ├── static/         # CSS, JS, images
 └── tests/          # JUnit tests
```

Additional files:
- `README.md` → project overview and setup
- `ARCHITECTURE.md` → system design documentation
- `skills/` → reusable workflow instructions for AI agents

---

## Architecture Guidelines

The application follows Spring MVC layered architecture.

### Controller Layer
- Handles HTTP requests and responses
- Should remain lightweight
- Avoid business logic in controllers

### Service Layer
- Contains business rules and validation
- Handles role-based workflows
- Reusable application logic belongs here

### Repository/DAO Layer
- Handles database interaction
- Uses JDBC for CRUD operations

### Frontend Layer
- Thymeleaf templates for rendering views
- Bootstrap for styling
- Reusable fragments should be preferred

---

## Security Rules

Authentication and authorization use Spring Security.

Roles:
- Non-members → view only
- Users → add board games and reviews
- Managers → edit/delete reviews

Do not bypass role validation.

---

## Development Workflow

When implementing features:

1. Update model/entity if required
2. Update repository/DAO layer
3. Update service layer
4. Update controller mappings
5. Update Thymeleaf templates
6. Add or update JUnit tests
7. Run validation commands

---

## Validation Commands

Build project:

```bash
mvn clean install
```

Run tests:

```bash
mvn test
```

Run application:

```bash
mvn spring-boot:run
```

---

## Coding Guidelines

- Follow existing package naming conventions
- Keep methods small and reusable
- Preserve separation of concerns
- Add tests for new business logic
- Avoid duplicate logic across controllers/services

---

## Common Tasks

Examples:
- Add board game feature
- Add review functionality
- Modify role permissions
- Update Thymeleaf views
- Add validation rules

See `skills/` directory for reusable workflows.

---

## Constraints

- Do not hardcode credentials
- Preserve Spring MVC architecture boundaries
- Avoid direct database logic in controllers
- Maintain role-based authorization behavior

---

## References

- `README.md`
- `ARCHITECTURE.md`
- `CONTRIBUTING.md`
- `skills/`
