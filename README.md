Project: WCP Execution API

Act as a Senior Java Architect and Cloud Platform Engineer.

Design and develop an enterprise-grade WCP Execution API (Workflow Control Platform) using Java and Spring Boot.

Business Objective

Build a centralized platform to upload CSV files containing SQL scripts to Google Cloud Storage (GCS), automatically trigger execution against Cloud SQL PostgreSQL, and provide complete execution visibility through APIs.

Technology Stack

- Java + Spring Boot
- Spring Data JPA
- PostgreSQL (Cloud SQL)
- Google Cloud Storage
- Eventarc
- Cloud Run Jobs
- React frontend integration
- Maven
- Docker
- Google Cloud Logging

Functional Requirements

1. CSV upload through REST APIs.
2. Store uploaded files in GCS.
3. Automatically detect new files through Eventarc.
4. Trigger SQL execution using Cloud Run Jobs.
5. Support DDL, DML, SQL statements and stored procedures.
6. Process multiple files independently.
7. Maintain execution history and audit logs.
8. Prevent duplicate file processing using GCS object generation.
9. Display command-level execution status and error messages.
10. Support selective retry of failed commands.

Execution and Dependency Management

- Execute independent SQL commands even if another command fails.
- Block commands whose dependencies have failed.
- Maintain command execution order where dependencies exist.
- Retry only eligible failed commands.
- Prevent unintended duplicate execution.
- Track PENDING, RUNNING, SUCCESS, FAILED and BLOCKED statuses.

API Requirements

Create REST endpoints for:

- File upload
- Job listing
- Job details
- Command execution details
- Job retry
- Execution logs
- Health checks

Use API versioning, request validation, centralized exception handling, structured logging and appropriate HTTP status codes.

Database Requirements

Design PostgreSQL tables for:

- Uploaded files
- Execution jobs
- SQL commands
- Command dependencies
- Execution attempts
- Audit history

Include appropriate indexes, foreign keys and transaction management.

Architecture and Code Quality

- Follow clean architecture and SOLID principles.
- Use appropriate design patterns.
- Separate controllers, services, repositories and execution components.
- Implement secure configuration and Secret Manager integration.
- Support concurrent execution safely.
- Include unit tests and integration tests.
- Include retry, timeout and failure handling.
- Avoid hardcoding credentials or SQL configuration.

Deliverables

1. Complete architecture diagram.
2. Maven project structure.
3. PostgreSQL schema and migration scripts.
4. Complete Java Spring Boot implementation.
5. REST API documentation using OpenAPI/Swagger.
6. Dockerfile.
7. GCP deployment instructions.
8. Cloud Run Jobs and Eventarc integration.
9. Unit and integration tests.
10. Production-readiness checklist.

Build this as a maintainable enterprise platform, not a basic demonstration project. Explain architectural decisions and generate implementation incrementally, validating each module before proceeding.
