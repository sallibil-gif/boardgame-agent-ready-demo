# BoardgameListingWebApp

## Overview

BoardgameListingWebApp is a full-stack Spring Boot web application for managing board games and reviews with role-based authentication and authorization.

Users can browse board games and reviews publicly, while authenticated users can add reviews and board games. Managers have additional permissions to edit and delete reviews.

---

## Features

- Full-stack Spring Boot application
- Board game listing and review management
- Authentication and authorization using Spring Security
- Role-based access control
- CRUD operations for board games and reviews
- Thymeleaf-based UI with Bootstrap styling
- AWS EC2 deployment
- JUnit testing support
- MVC layered architecture
- H2 in-memory database
## Development Workflow

1. Create feature branch
2. Implement changes
3. Run tests
4. Submit pull request
---

## User Roles

### Non-Members
- View board games
- View reviews

### Users
- Add board games
- Add reviews

### Managers
- Edit reviews
- Delete reviews

---

## Technology Stack

### Backend
- Java
- Spring Boot
- Spring MVC
- Spring Security
- JDBC

### Frontend
- Thymeleaf
- HTML5
- CSS
- JavaScript
- Bootstrap

### Database
- H2 Database Engine

### Testing
- JUnit

### Deployment
- AWS EC2

---

## Project Structure

```text
src/
 ├── controllers/
 ├── services/
 ├── repositories/
 ├── templates/
 ├── static/
 └── tests/
```

- controllers → request handling
- services → business logic
- repositories → database interaction
- templates → Thymeleaf UI
- static → CSS/JavaScript assets

---

## Installation

### Prerequisites

- Java 17+
- Maven

### Clone Repository

```bash
git clone <repository-url>
cd BoardgameListingWebApp
```

### Build Application

```bash
mvn clean install
```

### Run Application

```bash
mvn spring-boot:run
```

---

## Testing

Run unit tests:

```bash
mvn test
```

---

## Default Test Users

### User Role
- Username: bugs
- Password: bunny

### Manager Role
- Username: daffy
- Password: duck

---

## Architecture

The application follows Spring MVC layered architecture:

- Controller Layer
- Service Layer
- Repository/DAO Layer
- Database Layer

See `ARCHITECTURE.md` for detailed system design.

---

## Security

Authentication and authorization are implemented using Spring Security.

Authorization is role-based:
- Non-members
- Users
- Managers

---

## Deployment

The application can be deployed on:
- AWS EC2
- Docker containers
- Cloud platforms supporting Java/Spring Boot

---

## Contribution

See `CONTRIBUTING.md` for contribution guidelines.

---

## Agentic Development

This repository includes:
- `AGENTS.md` → AI agent guidance
- `skills/` → reusable AI workflows
- `ARCHITECTURE.md` → system architecture documentation

## Documentation

- AGENTS.md
- ARCHITECTURE.md
- CONTRIBUTING.md
- AGENTIC_SDLC_WORKFLOW.md
These files improve AI-assisted development workflows.
