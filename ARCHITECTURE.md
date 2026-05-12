# ARCHITECTURE.md

# BoardgameListingWebApp Architecture

## Overview

BoardgameListingWebApp is a full-stack Spring Boot web application that allows users to browse board games and reviews with role-based access control.

The application follows the Spring MVC architecture pattern and separates responsibilities into presentation, business, and data access layers.

---

# High-Level Architecture

User Browser
↓
Spring MVC Controllers
↓
Service Layer
↓
Repository / DAO Layer
↓
H2 Database

---

# Technology Stack

## Backend
- Java
- Spring Boot
- Spring MVC
- Spring Security
- JDBC

## Frontend
- Thymeleaf
- HTML5
- CSS
- JavaScript
- Bootstrap

## Database
- H2 In-Memory Database

## Testing
- JUnit

## Deployment
- AWS EC2

---

# Layered Architecture

## 1. Presentation Layer

Responsible for:
- Rendering UI
- Handling user requests
- Returning views

Components:
- Thymeleaf templates
- Controllers
- Static assets (CSS/JS)

Example responsibilities:
- Login page
- Boardgame list page
- Review submission form

---

## 2. Controller Layer

Responsible for:
- Receiving HTTP requests
- Calling services
- Returning views or redirects

Guidelines:
- Keep controllers lightweight
- Avoid business logic in controllers

Example:
- BoardgameController
- ReviewController

---

## 3. Service Layer

Responsible for:
- Business logic
- Validation
- Role-based workflow handling

Examples:
- Adding reviews
- Permission checks
- Boardgame management

Guidelines:
- Centralize application rules here
- Reuse services where possible

---

## 4. Repository / DAO Layer

Responsible for:
- Database interaction
- CRUD operations

Uses:
- JDBC

Examples:
- Fetch boardgames
- Insert reviews
- Update review data

---

## 5. Database Layer

Database:
- H2 In-Memory Database

Purpose:
- Store users
- Store boardgames
- Store reviews

Initialization:
- schema.sql
- initial seed data

---

# Authentication and Authorization

Implemented using Spring Security.

## Roles

### Non-Members
- View boardgames
- View reviews

### Users
- Add boardgames
- Add reviews

### Managers
- Edit reviews
- Delete reviews

---

# Request Flow

1. User accesses application
2. Controller receives request
3. Service layer processes business logic
4. Repository layer accesses database
5. Thymeleaf renders response
6. HTML returned to browser

---

# Testing Strategy

Testing framework:
- JUnit

Focus areas:
- Service logic
- Controller behavior
- Authentication flow

---

# Deployment Architecture

Application deployed on:
- AWS EC2

Deployment flow:
Developer → Maven Build → Spring Boot JAR → AWS EC2 Deployment

---

# Design Principles

- Separation of concerns
- MVC architecture
- Reusable Thymeleaf fragments
- Role-based security
- Layered application structure

---

# Future Improvements

Potential enhancements:
- Persistent database (PostgreSQL/MySQL)
- REST API support
- Docker containerization
- CI/CD pipeline integration
- OAuth authentication
- Cloud-native deployment
