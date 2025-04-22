# Nest.js Prompt Engineering Guide

## Introduction to Prompt Engineering for Nest.js

Prompt engineering can supercharge your Nest.js development workflow when using AI tools like Cursor or ChatGPT. By crafting precise and context-aware prompts, you can generate clean, structured, and scalable backend code that aligns with your team’s architecture and standards.

## Core Principles for Nest.js-Specific Prompts

### 1. Be Specific About the Module or Feature

**Basic prompt:**

```
Create a user module
```

**Improved prompt:**

```
Generate a Nest.js module named `UserModule` with:
- A `UserController` that handles GET, POST, PUT, and DELETE requests
- A `UserService` that encapsulates business logic
- A `UserEntity` with TypeORM decorators
- DTOs for create and update operations
- Proper dependency injection and TypeScript typing
```

### 2. Include Validation and Error Handling Requirements

**Improved prompt:**

```
Generate a Nest.js controller for `AuthController` that:
- Includes login and register routes
- Uses `class-validator` decorators on DTOs
- Throws `UnauthorizedException` for login failure
- Returns structured JSON responses
```

### 3. Specify the Database & ORM

**Improved prompt:**

```
Create a Nest.js service using Prisma ORM to manage products.
- Include methods to get all products, get by ID, create, update, and delete.
- Use proper DTOs and validation.
- Handle `NotFoundException` where appropriate.
```

### 4. Mention Middleware or Interceptors

**Improved prompt:**

```
Generate a Nest.js interceptor that logs the time taken to handle each request.
- Apply it globally using `APP_INTERCEPTOR`
- Include proper logging using Nest's built-in logger
```

### 5. Mention Module Structure & File Organization

**Improved prompt:**

```
Generate a feature module for handling blog posts.
Place files in:
- `/posts/posts.module.ts`
- `/posts/posts.controller.ts`
- `/posts/posts.service.ts`
- `/posts/dto/create-post.dto.ts`
- `/posts/entities/post.entity.ts`
```

## Prompt Templates for Common Nest.js Tasks

### CRUD Feature

```
Create a Nest.js CRUD module for managing [resource].

- Include Controller, Service, DTOs, and Entity
- Use [TypeORM/Prisma] for database operations
- Handle common errors with proper exceptions
- Return consistent JSON responses
- Follow NestJS best practices for file structure
```

### Authentication

```
Generate a JWT-based Auth system in Nest.js that includes:
- AuthController, AuthService, JwtStrategy
- Login and Register routes
- Password hashing with bcrypt
- JWT access tokens with expiration
- Guard for protecting routes
```

### Interceptor and Middleware

```
Create a Nest.js logging interceptor that:
- Logs method name, execution time, and status code
- Uses Nest's built-in Logger
- Is applied globally via `APP_INTERCEPTOR`
```

### Exception Filters

```
Generate a Nest.js HTTP exception filter that:
- Captures all unhandled exceptions
- Logs error stack
- Returns a standard error response
- Applies to all routes globally
```

### Define the Testing Framework and Scope

**Basic prompt:**

```
Write tests for user service
```

**Improved prompt:**

```
Write Jest test cases for a Nest.js `UserService` that:
- Includes methods: `createUser`, `getUserById`, `updateUser`, and `deleteUser`
- Mocks the `UserRepository` using `@nestjs/testing`
- Validates input using DTOs and class-validator
- Throws appropriate exceptions like `NotFoundException` and `ConflictException`
- Covers both success and failure scenarios
```

**Basic prompt:**

```
Add edge case tests
```

**Improved prompt:**

```
Add edge case test scenarios for `UserService` including:
- Creating a user that already exists (should throw `ConflictException`)
- Fetching a user with a non-existent ID (should throw `NotFoundException`)
- Updating a user with invalid data (should fail validation)
- Deleting a user that doesn't exist
```

**Provide reference testcase:**

```
If possible, start by writing one complete and properly structured test case that includes all necessary setup, mocking, and assertions. This test case should serve as a reference for others. Once it's written, use a prompt that explicitly asks the AI to follow the same structure and conventions as the example test case when generating additional test cases for other methods. This ensures consistency and helps maintain clean, maintainable test code.
```

## Prompt Refinement Best Practices

- **Ask for type safety**: “Add TypeScript types to DTOs and method signatures”
- **Request error handling**: “Include HTTP exceptions with custom messages”
- **Request testing**: “Add unit tests using Jest for the generated service”
- **Break complex prompts** into smaller steps for clarity and better output

## Do's and Don’ts

### ✅ Do:
- Specify controller routes and decorators
- Mention the exact ORM and its usage style
- Include expected return shapes
- Request DTOs with validation decorators

### ❌ Don’t:
- Ask for vague service generation without context
- Mix unrelated concerns (auth + CRUD + caching)
- Forget about exception handling and logging
```
