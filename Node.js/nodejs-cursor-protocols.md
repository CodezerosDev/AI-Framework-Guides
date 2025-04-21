# Protocols and Rules for Cursor AI with Node.js

## Configuring Cursor AI for Node.js Development

Proper Cursor settings ensure AI understands your Node.js project and follows your style and architecture.

## Initial Setup

### Include Project Paths
```
Settings > AI > Project Context > Add custom paths
- server.js or app.js
- routes/**/*.js
- controllers/**/*.js
- models/**/*.js
- middleware/**/*.js
- config/**/*.js
- package.json
```

### Enable JavaScript/TypeScript Analysis
```
Settings > Editor > Language Features > Enable TS Server
```

### Add Reference Documentation
```
Settings > AI > Project Context > Reference URLs
- https://nodejs.org/docs/latest-v18.x/api/
- https://expressjs.com/en/4x/api.html
- https://mongoosejs.com/docs/guide.html
```

## Custom Cursor Commands

### Create Route Command
```
Command: /node-route
Rule:
Generate Express.js routes in routes/{{name}}Routes.js with GET, POST, PUT, DELETE handlers.
```

### Create Model Command
```
Command: /node-model
Rule:
Generate a Mongoose model in models/{{name}}Model.js with schema and validation.
```

### Create Middleware Command
```
Command: /node-middleware
Rule:
Generate middleware in middleware/{{name}}Middleware.js. Must handle errors or auth.
```

## Input Filter Rules

- Enforce code style: Prettier, ESLint
- Require semicolons or no semicolons
- Format imports alphabetically

## Output Transformation Rules

### Extract Large Functions
```
Condition: Function > 50 lines
Action: Suggest splitting into multiple smaller functions.
```

### Add Error Handling
```
Pattern: Missing try/catch in async functions
Action: Wrap logic in try/catch and return responses with status codes.
```

## `.cursor` Configuration Example
```json
{
  "node": {
    "useFramework": "Express",
    "generateTests": true,
    "enableLinting": true
  },
  "cursor": {
    "contextInclude": [
      "server.js",
      "routes/**/*.js",
      "controllers/**/*.js"
    ],
    "contextExclude": ["node_modules/**", "dist/**"]
  }
}
```

## Keyboard Shortcuts

| Command                | Shortcut     | Description                          |
|------------------------|--------------|--------------------------------------|
| Generate Route         | Ctrl+Alt+R   | Runs `/node-route`                   |
| Generate Model         | Ctrl+Alt+M   | Runs `/node-model`                   |
| Generate Middleware    | Ctrl+Alt+W   | Runs `/node-middleware`              |
| Run Server             | Ctrl+Alt+S   | Executes `npm start`                 |
| Format Code            | Ctrl+Alt+F   | Runs `npm run lint:fix`              |
