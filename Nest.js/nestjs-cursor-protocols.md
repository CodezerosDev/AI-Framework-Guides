# Protocols and Rules for Cursor AI with Nest.js

## Setting Up Cursor AI for Nest.js Projects

Configuring Cursor correctly for a Nest.js backend helps ensure accurate code generation, consistent patterns, and reduced boilerplate. This document outlines all recommended settings and rules for backend development using Cursor AI.

## Initial Configuration

### Environment Setup

1. **Include Core Project Paths**

```
Settings > AI > Project Context > Add custom paths

Include:
- src/**/*.ts
- src/app.module.ts
- src/**/*.controller.ts
- src/**/*.service.ts
- src/**/*.module.ts
- src/**/*.entity.ts
- tsconfig.json
- package.json
```

2. **Enable TypeScript Analysis**

```
Settings > Editor > Language Features > Enable TypeScript Server
```

3. **Add Reference URLs**

```
Settings > AI > Project Context > Reference URLs

- https://docs.nestjs.com/
- https://typeorm.io/
- https://www.prisma.io/docs/
```

## Cursor Command Rules for Nest.js

### Create Module Command

```
Command: /nestjs-module

Rule:
Generate a Nest.js module named {{module_name}} with controller, service, DTOs, and an entity. Ensure TypeScript typing and validation.
```

### Create Auth Flow Command

```
Command: /nestjs-auth

Rule:
Generate a full JWT-based Auth system with login, register, bcrypt hashing, and guards. Use `PassportStrategy` and access token expiration.
```

### Create Middleware Command

```
Command: /nestjs-logger

Rule:
Generate a logging middleware that logs method, URL, and timestamp. Use NestJS Logger.
```

## Output Transformation Rules

### Extract Services and DTOs

```
Rule:
If Controller method count > 5 → extract to service
If DTO properties > 5 → create separate DTO files
```

### Exception Handling Rule

```
Pattern:
Missing try/catch or exception handling in services

Action:
Add NestJS HttpException or NotFoundException where needed
```

## Enforce Nest.js Style Guide

```
Settings > AI > Code Generation > Style enforcement > Nest.js

- PascalCase for services and controllers
- camelCase for variables
- Proper decorators on methods and parameters
```

## Example `.cursor` Configuration

```json
{
  "nestjs": {
    "useORM": "TypeORM",
    "generateDTOs": true,
    "generateValidation": true,
    "enableLinting": true
  },
  "cursor": {
    "contextInclude": ["src/**/*.ts", "package.json"],
    "contextExclude": ["dist/**", "node_modules/**"]
  }
}
```

## Keyboard Shortcuts

| Command | Shortcut | Description |
|---------|----------|-------------|
| Run Nest App | `Ctrl+Alt+N` | Run server via `npm run start:dev` |
| Generate Module | `Ctrl+Alt+M` | Run `/nestjs-module` |
| Generate Auth | `Ctrl+Alt+A` | Run `/nestjs-auth` |
