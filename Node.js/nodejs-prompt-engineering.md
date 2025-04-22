# Node.js Prompt Engineering Guide

## Introduction to Prompt Engineering for Node.js

Prompt engineering means crafting clear instructions to AI tools so they generate the code you need. In Node.js development, good prompts save time and produce reliable server-side code. This guide explains how to write effective prompts for various Node.js tasks.

## Core Principles for Node.js Prompts

### 1. Specify the Framework or Library

**Basic prompt:**

```
Create a server
```

**Improved prompt:**

```
Generate an Express.js server that listens on port 3000,
handles JSON requests, and includes error handling middleware.
```

### 2. Define the Feature Clearly

**Basic prompt:**

```
Create an API
```

**Improved prompt:**

```
Create a REST API endpoint GET /users that returns a JSON list
of users from a MongoDB collection using Mongoose.
Include proper error handling and response status codes.
```

### 3. Include Data Source Details

**Improved prompt:**

```
Generate a Node.js service using Sequelize ORM connected to
a PostgreSQL database. Implement methods to create, read,
update, and delete products with validation.
```

### 4. Mention Middleware and Tools

**Improved prompt:**

```
Add authentication middleware using Passport.js JWT strategy
to protect route POST /orders. Include token validation and
error responses for unauthorized access.
```

### 5. Provide File Structure Expectations

**Improved prompt:**

```
Structure the project with:
- server.js (entry point)
- routes/userRoutes.js
- controllers/userController.js
- models/userModel.js
- middleware/authMiddleware.js
```

## Prompt Templates for Common Node.js Tasks

### CRUD API

```
Create a Node.js CRUD API for [resource] using Express.js and Mongoose.
- Define routes in routes/[resource]Routes.js
- Implement controllers in controllers/[resource]Controller.js
- Create a Mongoose model in models/[resource]Model.js
- Include validation and error handling
```

### Authentication Flow

```
Generate authentication in Node.js with:
- JWT login (POST /auth/login)
- User registration (POST /auth/register)
- Protect routes using Passport.js JWT middleware
- Store users in MongoDB with password hashing (bcrypt)
```

### WebSocket Chat Server

```
Create a real-time chat server in Node.js using Socket.io.
- Set up server in server.js
- Handle connection and disconnection events
- Broadcast messages to all connected clients
- Include user join/leave notifications
```

### Microservice Example

```
Generate a Node.js microservice using Fastify that:
- Provides GET /health endpoint returning { status: 'ok' }
- Registers service with Consul for service discovery
- Includes graceful shutdown on SIGINT
```

### Testing Template

```
Create Jest tests for the user controller:
- Test GET /users returns the correct status and data
- Mock Mongoose model using jest.mock
- Test error cases for invalid database responses
```

**Basic prompt:**

```
Write tests for user service
```

**Improved prompt:**

```
Write Mocha + Chai test cases for a Node.js `userService.js` file that:
- Includes methods: `createUser`, `getUserById`, `updateUser`, and `deleteUser`
- Uses a `userModel` that interacts with MongoDB via Mongoose
- Mocks database operations using `sinon` or `proxyquire`
- Tests both successful responses and thrown errors
- Ensures proper validation logic is followed for each method
```

**Basic prompt:**

```
Add edge case tests
```

**Improved prompt:**

```
Write test cases for `userService` covering edge cases:
- Creating a user with an already registered email (should throw a duplicate key error)
- Getting a user with an invalid or non-existent ID (should return null or throw)
- Updating a user with missing required fields (should trigger validation error)
- Deleting a user that doesn't exist (should handle gracefully without crashing)
```

**Provide reference testcase:**

```
If possible, start by writing one complete and properly structured test case that includes all necessary setup, mocking, and assertions. This test case should serve as a reference for others. Once it's written, use a prompt that explicitly asks the AI to follow the same structure and conventions as the example test case when generating additional test cases for other methods. This ensures consistency and helps maintain clean, maintainable test code.
```

## Prompt Refinement Tips

- **Break down complex tasks**: Ask for one piece at a time.
- **Ask for examples**: “Show sample request and response.”
- **Iterate**: Refine prompts based on AI output errors.
- **Add comments**: Request inline comments in generated code.

## Do’s and Don’ts

### ✅ Do:

- Mention the exact library, version, and patterns.
- Specify routes, methods, and expected inputs/outputs.
- Ask for error handling and edge cases.
- Provide project structure in prompts.

### ❌ Don’t:

- Use vague terms like “make an API” without details.
- Combine too many unrelated tasks in one prompt.
- Omit database or framework details.
- Ignore security (e.g., validation, authentication).
