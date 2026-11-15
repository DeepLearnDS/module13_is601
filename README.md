# Module 13 – JWT Authentication with Client-Side Validation and Playwright E2E Testing

## Project Overview

This project implements user registration and login using JSON Web Tokens (JWT), with a FastAPI backend and a client-side frontend. Users can register an account, log in with their credentials, and receive a JWT after successful authentication.

The project also includes client-side form validation, automated end-to-end testing with Playwright, Docker deployment, and a GitHub Actions CI/CD workflow.

## Features

### 1. User Registration

- Register using a username, email address, and password.
- Validate user input.
- Check whether an email or username is already registered.
- Hash passwords before storing them in the database.
- Return a response after successful registration.

### 2. User Login

- Log in using valid account credentials.
- Verify passwords securely.
- Return a JWT after successful authentication.
- Return an HTTP 401 response when credentials are incorrect.

### 3. Frontend Validation

The frontend includes separate registration and login pages:

- `register.html`
- `login.html`

Client-side validation includes:

- Email format validation.
- Minimum password length validation.
- Feedback for invalid input and authentication errors.
- Handling of JWT responses and browser-side token storage.

### 4. Automated Testing

The project includes unit, integration, and end-to-end tests.

Playwright E2E tests cover:

- Successful user registration.
- Successful user login.
- Registration with an invalid or too-short password.
- Login with an incorrect password.

## Technologies Used

- Python 3.11
- FastAPI
- SQLAlchemy
- PostgreSQL
- Pydantic
- JSON Web Tokens (JWT)
- Password hashing
- HTML, CSS, and JavaScript
- Playwright
- Pytest
- Docker and Docker Compose
- GitHub Actions
- Trivy vulnerability scanning

## Project Setup

### Prerequisites

Install the following tools:

- Python 3.11
- Docker Desktop
- Docker Compose
- Git
- A GitHub account

### 1. Clone the Repository

```bash
git clone https://github.com/DeepLearnDS/module13_is601.git
cd module13_is601
```

### 2. Configure Environment Variables

Create and configure the environment file required by the application.

Use the environment variable names and settings expected by the project's configuration. Do not commit passwords, database credentials, JWT secrets, or other sensitive information to GitHub.

### 3. Start the Application with Docker Compose

Build and start the application:

```bash
docker compose up --build -d
```

Check the running containers:

```bash
docker compose ps
```

View application logs:

```bash
docker compose logs -f web
```

Stop the containers:

```bash
docker compose down
```

## Running Tests

Run the test suite using the project's Docker environment:

```bash
docker compose run --rm web python -m pytest
```

Run integration tests:

```bash
docker compose run --rm web python -m pytest tests/integration -v
```

Run unit tests:

```bash
docker compose run --rm web python -m pytest tests/unit -v
```

Run end-to-end tests:

```bash
docker compose run --rm web python -m pytest tests/e2e -v
```

The E2E tests use Playwright to verify registration, login, and invalid-input scenarios.

## Frontend Pages

The application includes two separate frontend pages:

- **Registration:** `register.html`
- **Login:** `login.html`

The pages provide form validation and feedback for users during registration and login. Successful authentication returns a JWT that the frontend handles for subsequent authenticated requests.

Use the application's configured frontend routes or instructions to open these pages.

## Docker Deployment

The application is containerized using Docker and Docker Compose.

Build the Docker image:

```bash
docker build -t app:test .
```

Run the Docker image:

```bash
docker run --rm -p 8000:8000 app:test
```

### Docker Hub

Docker Hub repository:

[https://hub.docker.com/r/codeec/601_module13](https://hub.docker.com/r/codeec/601_module13)

## GitHub Actions CI/CD

The project uses GitHub Actions to automate testing and deployment.

The workflow is designed to:

1. Set up the Python environment.
2. Start the required database and application services.
3. Run automated tests, including Playwright E2E tests.
4. Build the Docker image.
5. Run a Trivy vulnerability scan.
6. Push the Docker image to Docker Hub after the required checks succeed.

Docker Hub credentials are configured through GitHub repository secrets:

- `DOCKERHUB_USERNAME`
- `DOCKERHUB_TOKEN`

The workflow uses these secrets to authenticate with Docker Hub. Sensitive credentials should never be committed to the repository.

## Security

Security measures implemented in the project include:

- Password hashing rather than storing plain-text passwords.
- JWT-based authentication.
- Input validation using Pydantic and client-side validation.
- Updated Python package dependencies.
- Docker image vulnerability scanning using Trivy.
- GitHub Actions secrets for Docker Hub authentication.

## Learning Objectives

This assignment provides practical experience with:

- Implementing JWT authentication.
- Building registration and login functionality.
- Validating user input on the client and server.
- Testing frontend workflows with Playwright.
- Integrating automated tests into GitHub Actions.
- Building and publishing Docker images.
- Scanning container images for security vulnerabilities.

## Repository

GitHub:

[https://github.com/DeepLearnDS/module13_is601](https://github.com/DeepLearnDS/module13_is601)

Docker Hub:

[https://hub.docker.com/r/codeec/601_module13](https://hub.docker.com/r/codeec/601_module13)
