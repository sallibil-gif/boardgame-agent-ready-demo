# BoardgameListingWebApp — Agentic SDLC Workflow Documentation

# Overview

This document explains how the BoardgameListingWebApp repository was transformed into an AI-agent-ready repository using Agentic SDLC practices.

The work involved:

* Improving repository documentation
* Adding AI guidance files
* Creating reusable AI workflows (skills)
* Running repository AI-readiness assessment using agentready
* Improving repository engineering standards

The goal was to make the repository easier for:

* AI agents
* Developers
* New contributors
* Automated workflows

to understand, navigate, and modify safely.

---

# Original Repository

Repository:

* BoardgameListingWebApp

Technology Stack:

* Java
* Spring Boot
* Spring MVC
* Spring Security
* Thymeleaf
* H2 Database
* Maven
* AWS EC2

Application Purpose:

* Board game listing and review platform
* Role-based authentication and authorization
* Users can add board games and reviews
* Managers can edit/delete reviews

---

# Objective

The objective was to complete the following Agentic SDLC tasks:

1. Create AGENTS.md
2. Run agentready assessment
3. Create reusable AI skills

These tasks improve repository operability for AI-assisted software development.

---

# Task 1 — Create AGENTS.md

## Purpose

AGENTS.md helps AI agents understand:

* repository structure
* workflow expectations
* coding conventions
* validation commands
* architecture boundaries

It acts as an operational guide for AI contributors.

---

## Files Added

### README.md Improvements

Enhanced README with:

* Installation section
* Testing section
* Architecture section
* Development workflow section
* Agentic SDLC section

Purpose:

* Improve repository usability
* Improve documentation quality
* Help both humans and AI agents

---

### AGENTS.md

Added:

* Repository structure explanation
* Spring MVC architecture rules
* Security rules
* Development workflow
* Validation commands
* Coding guidelines
* Common tasks

Purpose:

* Help AI understand how to work safely inside repository
* Reduce AI confusion and incorrect implementations

---

### ARCHITECTURE.md

Documented:

* Layered architecture
* Controller layer
* Service layer
* Repository layer
* Database layer
* Authentication flow
* Request flow

Purpose:

* Help AI understand system design
* Prevent incorrect code placement
* Improve architectural consistency

---

### CONTRIBUTING.md

Added:

* Contribution workflow
* Validation rules
* Development expectations

Purpose:

* Standardize contribution process
* Improve repository onboarding

---

# Task 2 — Run agentready

## Purpose

agentready is an AI-readiness assessment tool.

It evaluates:

* Documentation quality
* Repository structure
* Workflow maturity
* Contributor guidance
* Automation readiness
* AI operability

---

## Initial Problems

Several environment-related issues occurred:

### SELinux Permission Issues

Problem:

* Podman container could not access mounted directories

Fix:

* Added :Z volume labels

---

### Git Safe Directory Issues

Problem:

* Git reported dubious ownership inside container

Fix:

* Configured safe.directory environment variable

---

### Rootless Podman Permission Issues

Problem:

* Container write access failures

Fix:

* Used --userns=keep-id

---

### Java Compatibility Issue

Problem:

* Spring Boot project failed on Java 21
* Error:
  NoSuchFieldError: JCTree$JCImport

Cause:

* Older Spring Boot/compiler dependencies incompatible with Java 21

Fix:

* Used Java 17 containerized Maven environment

Container Command:

```bash
podman run --rm \
  -v $(pwd):/workspace:Z \
  -w /workspace \
  docker.io/maven:3.9.6-eclipse-temurin-17 \
  mvn clean install
```

Purpose:

* Avoid modifying office Fedora system Java version
* Use isolated compatible build environment

---

## agentready Assessment Workflow

Command Used:

```bash
podman run --rm \
  --userns=keep-id \
  -e HOME=/tmp \
  -e GIT_CONFIG_COUNT=1 \
  -e GIT_CONFIG_KEY_0=safe.directory \
  -e GIT_CONFIG_VALUE_0=/repo \
  -v $(pwd):/repo:Z \
  ghcr.io/ambient-code/agentready:latest \
  assess /repo --output-dir /repo/agentready-reports
```

---

## Initial Score

Initial Score:

* 32.4/100

Problems detected:

* Missing AGENTS.md improvements
* Missing skills
* Missing ADRs
* Missing contribution templates
* Missing workflow standards

---

## Improvements Added

### ADR Documentation

Created:

* docs/adr/0001-project-architecture.md
* docs/adr/0002-security-architecture.md
* docs/adr/0003-template-engine-choice.md

Purpose:

* Document architectural decisions
* Improve repository maintainability

---

### Pull Request Templates

Added:

* .github/pull_request_template.md

Purpose:

* Standardize pull requests
* Improve contribution consistency

---

### Issue Templates

Added:

* bug_report.md
* feature_request.md

Purpose:

* Improve issue quality
* Standardize reporting process

---

### Pre-Commit Configuration

Added:

* .pre-commit-config.yaml

Purpose:

* Improve code quality automation

---

### Conventional Commit Support

Added:

* .commitlintrc.yml

Purpose:

* Encourage consistent commit messages

---

### Makefile

Added:

* setup command
* test command
* run command

Purpose:

* Simplify developer workflow
* Improve automation readiness

---

## Final Score

Final Score:

* 54.7/100

Result:

* Significant repository AI-readiness improvement
* Improved documentation maturity
* Improved contributor workflow maturity
* Improved AI-agent operability

---

# Task 3 — Create AI Skills

## Purpose

Skills provide reusable workflow instructions for AI agents.

They reduce:

* token usage
* workflow discovery effort
* repeated repository investigation
* inconsistent implementations

Skills help AI agents perform repository-specific tasks reliably.

---

## Skills Implemented

### Skill 1 — Add Review Feature

Location:

* skills/add-review/SKILL.md

Workflow:

* Update entity/model
* Update DAO layer
* Update service layer
* Update controller
* Update Thymeleaf templates
* Add JUnit tests
* Run validation

Purpose:

* Standardize review feature implementation

---

### Skill 2 — Add Boardgame Feature

Location:

* skills/add-boardgame/SKILL.md

Workflow:

* Update boardgame model
* Update repository layer
* Update service layer
* Update controllers
* Update UI templates
* Add tests

Purpose:

* Reusable feature implementation workflow

---

### Skill 3 — Run Application

Location:

* skills/run-application/SKILL.md

Workflow:

* Build project
* Run Spring Boot application
* Verify localhost deployment

Purpose:

* Simplify local development setup

---

# Final Repository Structure

```text
BoardgameListingWebApp/
│
├── README.md
├── AGENTS.md
├── ARCHITECTURE.md
├── CONTRIBUTING.md
│
├── docs/
│   └── adr/
│
├── skills/
│   ├── add-review/
│   ├── add-boardgame/
│   └── run-application/
│
├── .github/
│   ├── ISSUE_TEMPLATE/
│   └── pull_request_template.md
│
├── agentready-reports/
│
├── .pre-commit-config.yaml
├── .commitlintrc.yml
├── Makefile
│
└── src/
```

---

# Key Learnings

## Agentic SDLC Concepts

Learned:

* AI-agent-ready repositories
* AGENTS.md purpose
* Skills workflow design
* Repository AI operability
* Architectural documentation
* Contributor workflow maturity

---

## DevOps and Container Troubleshooting

Learned:

* SELinux container permissions
* Podman rootless container issues
* Git safe.directory configuration
* Java version compatibility
* Containerized development workflow

---

## AI Workflow Optimization

Learned:

* Reducing AI confusion
* Standardizing repository workflows
* Reusable AI instructions
* Improving deterministic AI behavior

---

# Final Outcome

The repository was transformed from:

* Human-readable project

into:

* AI-agent-operable repository

The repository now supports:

* AI-assisted development
* Reusable workflows
* Improved contributor onboarding
* Better repository documentation
* Standardized engineering practices
* Measurable AI-readiness improvements

---

# Summary

Tasks Completed:

* Task 1 — Create AGENTS.md ✅
* Task 2 — Run agentready ✅
* Task 3 — Create AI Skills ✅

Final Result:

* Successfully implemented Agentic SDLC practices into BoardgameListingWebApp repository.

