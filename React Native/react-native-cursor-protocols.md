# Protocols and Rules for Cursor AI with React Native

## Setting Up Cursor AI for Optimal React Native Development

Cursor AI can significantly enhance your React Native development workflow when configured properly. This guide outlines specific configurations, rules, and best practices to optimize Cursor for React Native projects.

## Initial Configuration

### Environment Setup

1. **Configure React Native Project Paths**
   
   Ensure Cursor AI is aware of your React Native project structure:
   
   ```
   Settings > AI > Project Context > Add custom paths > [path to your React Native project]
   ```
   
   Recommended paths to include:
   - src/ (or your main code directory)
   - package.json
   - tsconfig.json (if using TypeScript)
   - metro.config.js
   - babel.config.js

2. **Set JavaScript/TypeScript Analysis Integration**

   For better code intelligence:
   
   ```
   Settings > Editor > Language Features > JavaScript/TypeScript > Enable TypeScript Server integration
   ```

3. **Include Relevant Package Documentation**

   Add popular React Native packages to your project context:
   
   ```
   Settings > AI > Project Context > Add reference URLs
   ```
   
   Recommended URLs:
   - https://reactnative.dev/docs
   - https://reactnavigation.org/docs
   - https://redux.js.org/
   - https://styled-components.com/docs

## Cursor Command Rules for React Native

Create custom commands in Cursor to streamline React Native development:

### Custom React Native Commands

1. **Create Functional Component**

   Command: `/rn-component`
   
   Rule configuration:
   ```
   Generate a React Native functional component named {{component_name}} with:
   - Proper TypeScript props interface
   - StyleSheet for component styles
   - Memoization for performance optimization
   - Basic component documentation
   ```

2. **Create Screen Component**

   Command: `/rn-screen`
   
   Rule configuration:
   ```
   Generate a React Native screen component named {{screen_name}} including:
   - Navigation props typing
   - Safe area handling
   - Basic layout structure with styles
   - Loading and error states
   - Screen-level documentation
   ```

3. **Generate Custom Hook**

   Command: `/rn-hook`
   
   Rule configuration:
   ```
   Create a React Native custom hook named {{hook_name}} with:
   - Proper TypeScript typing
   - Performance optimization with useMemo/useCallback
   - Return value interface
   - Hook documentation with usage example
   ```

4. **React Native Test Template**

   Command: `/rn-test`
   
   Rule configuration:
   ```
   Generate a React Native test file for {{test_subject}} with:
   - Jest and React Native Testing Library setup
   - Mock implementations for native modules
   - Common test cases and assertions
   - Snapshot testing configuration
   ```

## Cursor Chat Context Rules

Configure how Cursor processes React Native-specific context for more accurate assistance:

### Project Structure Context

Enable Cursor to understand your React Native project structure:

```
Settings > AI > Project Context > Directory Structure > Enable
```

Set specific file inclusion patterns:
```
Include: 
- src/**/*.{js,jsx,ts,tsx}
- components/**/*.{js,jsx,ts,tsx}
- screens/**/*.{js,jsx,ts,tsx}
- App.{js,jsx,ts,tsx}
- package.json
- metro.config.js
- babel.config.js
- tsconfig.json
- ios/Podfile
- android/build.gradle
```

### Code Generation Context Limits

Set maximum token limits for generated React Native code:

```
Settings > AI > Context Settings > Maximum generated code size > 2500 tokens
```

This prevents Cursor from generating overly complex components that may be difficult to maintain.

### Dependency Analysis

Enable dependency scanning to help Cursor understand your project dependencies:

```
Settings > AI > Project Context > Analyze dependencies > Enable
```

## Input Filter Rules

Configure input filtering rules to ensure Cursor adheres to React Native best practices:

### Enforce React Native Style Guide

Create a rule that ensures generated code follows React Native style conventions:

```
Settings > AI > Code Generation > Style enforcement > React Native
```

This will apply rules like:
- Two-space indentation
- Proper component naming conventions
- StyleSheet object usage patterns
- Import ordering

### State Management Consistency

Set up a rule to maintain consistency with your chosen state management approach:

```
Settings > AI > Project Rules > Add rule > "State Management Consistency"

Rule definition:
{
  "pattern": "state management",
  "enforce": "{{preferred_state_management}}",
  "allowed_values": ["Redux", "Context API", "MobX", "Recoil", "Zustand"]
}
```

## Output Transformation Rules

Configure how Cursor's output is formatted for React Native development:

### Component Extraction Rule

Set up a rule to automatically extract large components into smaller ones:

```
Settings > AI > Code Transformation > Add rule > "Component Extraction"

Rule definition:
{
  "condition": "Component exceeds 100 lines",
  "action": "Extract subcomponents into separate files",
  "naming_convention": "{{ParentComponent}}{{PurposeName}}"
}
```

### Performance Optimization Rule

Create a rule to optimize React Native rendering performance:

```
Settings > AI > Code Transformation > Add rule > "React Native Performance"

Rule definition:
{
  "patterns": [
    "FlatList without key extractor",
    "Missing memo() for list items",
    "Inline styles in render function",
    "Anonymous function in render"
  ],
  "action": "Suggest optimized implementation"
}
```

## React Native-Specific Editor Settings

Fine-tune Cursor's editor for React Native development:

### Code Completion Settings

```
Settings > Editor > Code Completion > React Native

Configuration:
- Enable component prop completion
- Suggest required props first
- Show inline documentation for components
- Auto-import React Native components
```

### Code Action Settings

```
Settings > Editor > Code Actions > React Native

Enable:
- Extract component refactoring
- Convert to functional component
- Wrap with Fragment/View
- Add style property suggestions
```

## Problem Recognition Patterns

Configure Cursor to recognize common React Native issues:

### Common React Native Errors

```
Settings > AI > Problem Recognition > Add patterns

Patterns:
- "Cannot read property 'style' of undefined"
- "Invariant Violation: ViewPropTypes"
- "Metro bundler error"
- "Native module cannot be null"
```

For each pattern, configure Cursor to suggest appropriate fixes and explanations.

## Project-Level Configuration

Create a `.cursor` configuration file at your project root for team-wide settings:

```json
{
  "reactNative": {
    "enableLinting": true,
    "lintRules": [
      "react-native/no-inline-styles",
      "react-native/no-color-literals",
      "react-hooks/exhaustive-deps"
    ],
    "componentExtraction": {
      "threshold": 100,
      "enabled": true
    },
    "stateManagement": "Redux",
    "generateDocumentation": true
  },
  "cursor": {
    "contextInclude": [
      "src/**/*.{js,jsx,ts,tsx}",
      "package.json",
      "metro.config.js"
    ],
    "contextExclude": [
      "node_modules/**",
      "android/**",
      "ios/**",
      "build/**"
    ]
  }
}
```

## Keyboard Shortcuts and Commands

Configure React Native-specific keyboard shortcuts in Cursor:

### Recommended Shortcuts

| Command | Shortcut | Description |
|---------|----------|-------------|
| RN Metro Reload | `Ctrl+Alt+R` | Triggers Metro bundler reload |
| Format Component | `Ctrl+Alt+F` | Properly formats component structure |
| Extract Component | `Ctrl+Alt+C` | Extracts selected code into a new component |
| Navigate to Definition | `F12` | Jump to component or function definition |
| Insert RN Snippet | `Ctrl+Space` | Access React Native-specific code snippets |

## Debugging Integration

Configure Cursor for optimal React Native debugging experience:

### Debug Configuration

```
Settings > Debugging > React Native

Options:
- Enable Metro bundler integration
- Track component re-renders
- Performance monitoring
- Network request inspection
```

## Metro Bundler Integration

Configure Cursor to work effectively with Metro Bundler:

```
Settings > Tools > React Native > Metro Bundler

Configuration:
- Auto-start Metro on project open
- Enable Fast Refresh
- Show Metro output in editor
- Custom Metro configuration path
```

## Platform-Specific Settings

Configure platform-specific behaviors for iOS and Android:

```
Settings > AI > Platform Settings > iOS/Android

iOS Settings:
- Cocoapods integration
- iOS simulator startup options
- iOS-specific styling defaults

Android Settings:
- Gradle integration settings
- Android emulator options
- Material Design preferences
```

## Code Snippet Library

Create a custom React Native code snippet library:

```
Settings > Editor > Snippets > React Native

Add snippets for:
- FlatList with performance optimizations
- Common form components
- Navigation boilerplate
- Animation templates
- Platform-specific code
```

## Conclusion

By implementing these protocols and rules for Cursor AI, you'll create a more efficient React Native development environment. These configurations help ensure consistency, reduce errors, and leverage React Native-specific features to their fullest potential.

Remember to update these settings as your project evolves and as new React Native or Cursor features become available.
