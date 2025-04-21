# React Native Prompt Engineering Guide

## Introduction to Prompt Engineering for React Native

Effective prompt engineering can significantly enhance your React Native development workflow when using AI tools like Cursor. This guide provides best practices for crafting prompts specifically tailored for React Native development.

## Core Principles for React Native-Specific Prompts

### 1. Be Specific About Component Type

React Native uses different component types for different purposes:

**Basic prompt:**
```
Create a list component
```

**Improved prompt:**
```
Create a React Native FlatList component that displays user profiles with images, names, and status indicators. Include pull-to-refresh functionality, infinite scrolling with activity indicator, and empty state handling. The component should be optimized for performance with appropriate item recycling.
```

### 2. Include State Management Context

Specify your state management approach for better contextual responses:

**Basic prompt:**
```
Generate code for a login screen
```

**Improved prompt:**
```
Generate a React Native login screen using Redux for state management. The screen should include email and password fields with validation, a submit button with loading state, error handling for authentication failures, and "Forgot Password" functionality. Use Redux actions and reducers for handling the authentication flow.
```

### 3. Define Platform-Specific Requirements

React Native's cross-platform nature often requires platform-specific adaptations:

**Basic prompt:**
```
Create a notification component
```

**Improved prompt:**
```
Create a React Native notification system that handles both iOS and Android notifications appropriately. Include logic for requesting permissions, token registration, and notification handling for both foreground and background states. For iOS, handle the required permission flow, and for Android, include the necessary channel creation code. Use react-native-notifications package.
```

### 4. Specify Package Dependencies

Clearly indicate which React Native packages you're using:

**Basic prompt:**
```
Create navigation code
```

**Improved prompt:**
```
Create a React Native navigation setup using React Navigation v6 with a bottom tab navigator, drawer navigator, and stack navigator. Include type definitions for TypeScript, custom header components, and navigation params. Set up deep linking configuration and navigation state persistence using AsyncStorage.
```

### 5. Describe Desired Styling Approach

React Native offers multiple styling options - be explicit:

**Basic prompt:**
```
Style a button
```

**Improved prompt:**
```
Create a custom React Native button component using styled-components. The button should have primary, secondary, and disabled states with appropriate color transitions. Include proper ripple effects on Android and opacity animations on iOS. Make it support various sizes (small, medium, large) and include icons as an optional prop.
```

## Prompt Templates for Common React Native Tasks

### Creating a New Screen

```
Create a React Native screen named [ScreenName] that serves as a [purpose of screen].

Technical specifications:
- State management: [Redux/Context API/MobX/etc.]
- Navigation: [React Navigation/React Native Navigation]
- Dependencies: [list relevant packages]
- TypeScript: [Yes/No]

The screen should include:
- [List of UI components]
- [Interaction behaviors]
- [API calls if applicable]

Style guide:
- [Styling approach: StyleSheet/styled-components/etc.]
- [Color scheme references]
- [Typography specifications]
```

### Debugging Component Issues

```
Debug the following React Native component issue:

Code:
[paste problematic code]

Error message:
[paste error]

Behavior I'm seeing:
[describe the incorrect behavior]

Expected behavior:
[describe what you want to happen]

Environment:
- React Native version: [version]
- Platform: [iOS/Android]
- Device/emulator: [specifics]
```

### Custom Animation Implementation

```
Create a React Native animation for [describe what you want to animate].

Animation specifications:
- Library: [Animated API/React Native Reanimated/Lottie]
- Duration: [timeframe]
- Easing: [linear/ease-in/custom]
- Trigger: [on mount/on press/etc.]
- Visual behavior: [detailed description]

The animation should work with the following component structure:
[describe component tree or paste code]
```

## Best Practices for Refining Generated React Native Code

1. **Request Component Extraction**: Ask AI to extract reusable components from complex screens

2. **Ask for Test Coverage**: Request tests for generated components
   ```
   Add Jest and React Native Testing Library tests for the above FlatList component that verify rendering, user interactions, and edge cases
   ```

3. **Request Performance Considerations**:
   ```
   Refactor this code to optimize for performance by implementing memo, useCallback for event handlers, and proper list item rendering optimization
   ```

4. **Prompt for Documentation**:
   ```
   Add JSDoc comments to all component props, functions, and complex logic sections
   ```

5. **Ask for Alternative Approaches**:
   ```
   What alternative implementations could achieve the same result but with better [performance/readability/maintainability]?
   ```

## React Native-Specific Prompt Do's and Don'ts

### Do's:
- Specify React Native and dependency versions when version-specific features are needed
- Provide your project structure for context-aware code generation
- Include UI mockups or design system references
- Mention target platforms (iOS, Android, both) for platform-optimized code
- Reference specific sections from React Native documentation when applicable

### Don'ts:
- Avoid vague component descriptions ("make it look good" or "standard design")
- Don't omit state management approach, as this fundamentally affects implementation
- Avoid mixing unrelated concerns in a single prompt
- Don't request native module implementations without providing native code context
- Avoid requesting deprecated APIs without acknowledging the deprecation

## Advanced Prompt Strategies

### 1. Using Iterative Refinement
Start with a basic implementation and progressively enhance it:

```
// Initial prompt
Create a basic React Native form for user registration with email and password fields

// Follow-up prompts
1. Add form validation using Formik and Yup
2. Enhance the form with keyboard handling and focus management
3. Implement error handling and success states with appropriate visual feedback
```

### 2. Context-Building for Complex Features

```
I'm building a React Native e-commerce app with the following structure:
- User authentication using Firebase
- Product catalog with categories and filtering
- Shopping cart using Redux
- Order processing with Stripe SDK

Now, help me implement the shopping cart functionality with:
1. Add to cart animation
2. Quantity adjustments with visual feedback
3. Persistent cart storage using Redux Persist
4. Price calculation with tax and shipping estimates
```

### 3. Specifying Code Organization

```
Generate a React Native ProductDetail screen following clean architecture principles with:
- Components folder for UI elements
- Hooks folder for business logic
- Utils folder for helper functions
- Types folder for TypeScript interfaces

Each component should be in its own file with index exports.
```

### 4. Platform-Specific Implementation Requests

```
Create a React Native image picker component that:

1. For iOS:
   - Handles camera permissions properly
   - Uses UIImagePickerController via react-native-image-picker
   - Supports photo library and camera access
   - Handles iOS 14+ privacy requirements

2. For Android:
   - Implements proper runtime permissions
   - Handles URI paths correctly for different Android versions
   - Supports both gallery and camera intents
   - Works with scoped storage on Android 10+

The component should provide a unified API despite platform differences.
```

### 5. Performance-Focused Prompts

```
Optimize the following React Native FlatList implementation for performance:

[paste code]

Focus on:
1. Implementing proper item rendering optimization
2. Reducing unnecessary re-renders
3. Optimizing image loading and caching
4. Improving scroll performance with appropriate configuration
5. Minimizing JS thread blocking operations
```

## React Native-Specific Prompt Categories

### Navigation Prompts

```
Set up a React Navigation v6 configuration with:
- Bottom tabs for [list main tabs]
- Stack navigator for each tab flow
- Authentication flow with conditional rendering
- Custom transition animations
- TypeScript type definitions for route params
- Deep linking configuration

Follow best practices for navigation state management and screen mounting/unmounting optimization.
```

### Native Module Integration Prompts

```
Create a React Native bridge for the following native functionality:

Native Android code:
[paste Java/Kotlin code]

Native iOS code:
[paste Objective-C/Swift code]

The JavaScript interface should:
- Be fully typed with TypeScript
- Handle errors gracefully
- Support both promise and callback patterns
- Include proper resource cleanup
```

### Styling System Prompts

```
Create a comprehensive React Native styling system using [StyleSheet/styled-components/other] that:
- Implements our design tokens (colors, spacing, typography)
- Supports dark/light theme switching
- Handles different device sizes with responsive values
- Provides component-specific style utilities
- Maintains type safety with TypeScript

Include examples of the system applied to Button, Card, and Typography components.
```

## Conclusion

Effective prompt engineering for React Native development requires specificity about components, state management, platform requirements, and styling approaches. By following these guidelines, you can generate more accurate, useful, and maintainable React Native code using AI assistants.
