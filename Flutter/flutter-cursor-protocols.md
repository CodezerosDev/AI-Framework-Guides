# Protocols and Rules for Cursor AI with Flutter

## Setting Up Cursor AI for Optimal Flutter Development

Cursor AI can significantly enhance your Flutter development workflow when configured properly. This guide outlines specific configurations, rules, and best practices to optimize Cursor for Flutter projects.

## Initial Configuration

### Environment Setup

1. **Configure Flutter SDK Path**
   
   Ensure Cursor AI is aware of your Flutter SDK location:
   
   ```
   Settings > AI > Project Context > Add custom paths > [path to your Flutter SDK]
   ```
   
   This helps Cursor understand Flutter's native widgets and API.

2. **Set Dart Analysis Server Integration**

   For better code intelligence:
   
   ```
   Settings > Editor > Language Features > Dart > Enable Analysis Server integration
   ```

3. **Include Relevant Package Documentation**

   Add popular Flutter packages to your project context:
   
   ```
   Settings > AI > Project Context > Add reference URLs
   ```
   
   Recommended URLs:
   - https://pub.dev/documentation/flutter/latest/
   - https://api.flutter.dev/
   - https://docs.flutter.dev/cookbook

## Cursor Command Rules for Flutter

Create custom commands in Cursor to streamline Flutter development:

### Custom Flutter Commands

1. **Create Stateless Widget**

   Command: `/flutter-stateless`
   
   Rule configuration:
   ```
   Generate a Flutter stateless widget named {{widget_name}} with:
   - Proper constructor with required parameters
   - Consistent style using const constructors where possible
   - Widget structure following Material design guidelines
   - Proper documentation comments
   ```

2. **Create Stateful Widget**

   Command: `/flutter-stateful`
   
   Rule configuration:
   ```
   Generate a Flutter stateful widget named {{widget_name}} including:
   - Proper state class with lifecycle methods
   - Clean separation between widget and state
   - Appropriate dispose method implementation
   - Documentation for both widget and state classes
   ```

3. **Generate Model Class**

   Command: `/flutter-model`
   
   Rule configuration:
   ```
   Create a Dart model class for Flutter with:
   - JSON serialization/deserialization
   - Immutable implementation with copyWith method
   - toString, equality, and hashCode overrides
   - Factory constructors as needed
   ```

4. **Flutter Test Template**

   Command: `/flutter-test`
   
   Rule configuration:
   ```
   Generate a Flutter test file for {{test_subject}} with:
   - Appropriate test groups
   - Widget test setup with MaterialApp wrapper
   - Mock dependencies using Mockito or mocktail
   - Common test scenarios for the widget or class
   ```

## Cursor Chat Context Rules

Configure how Cursor processes Flutter-specific context for more accurate assistance:

### Project Structure Context

Enable Cursor to understand your Flutter project structure:

```
Settings > AI > Project Context > Directory Structure > Enable
```

Set specific file inclusion patterns:
```
Include: 
- lib/**/*.dart
- test/**/*.dart
- pubspec.yaml
- analysis_options.yaml
- ios/Runner/Info.plist
- android/app/src/main/AndroidManifest.xml
```

### Code Generation Context Limits

Set maximum token limits for generated Flutter code:

```
Settings > AI > Context Settings > Maximum generated code size > 2000 tokens
```

This prevents Cursor from generating overly complex widgets that may be difficult to maintain.

### Dependency Analysis

Enable dependency scanning to help Cursor understand your project dependencies:

```
Settings > AI > Project Context > Analyze dependencies > Enable
```

## Input Filter Rules

Configure input filtering rules to ensure Cursor adheres to Flutter best practices:

### Enforce Flutter Style Guide

Create a rule that ensures generated code follows Flutter style conventions:

```
Settings > AI > Code Generation > Style enforcement > Flutter
```

This will apply rules like:
- Two-space indentation
- Trailing commas for multi-line parameter lists
- Proper widget tree formatting
- Widget parameter alignment

### State Management Consistency

Set up a rule to maintain consistency with your chosen state management approach:

```
Settings > AI > Project Rules > Add rule > "State Management Consistency"

Rule definition:
{
  "pattern": "state management",
  "enforce": "{{preferred_state_management}}",
  "allowed_values": ["Provider", "Bloc", "Riverpod", "GetX", "Redux"]
}
```

## Output Transformation Rules

Configure how Cursor's output is formatted for Flutter development:

### Widget Extraction Rule

Set up a rule to automatically extract large widgets into separate methods:

```
Settings > AI > Code Transformation > Add rule > "Widget Extraction"

Rule definition:
{
  "condition": "Widget tree depth > 5 levels",
  "action": "Extract child widgets into separate build methods",
  "naming_convention": "build{{WidgetPurpose}}"
}
```

### Performance Optimization Rule

Create a rule to optimize Flutter rendering performance:

```
Settings > AI > Code Transformation > Add rule > "Flutter Performance"

Rule definition:
{
  "patterns": [
    "ListView without .builder",
    "Missing const constructors",
    "AnimationController without dispose"
  ],
  "action": "Suggest optimized implementation"
}
```

## Flutter-Specific Editor Settings

Fine-tune Cursor's editor for Flutter development:

### Code Completion Settings

```
Settings > Editor > Code Completion > Flutter

Configuration:
- Enable widget parameter completion
- Suggest required widget parameters first
- Show inline documentation for Flutter widgets
- Auto-import material packages
```

### Code Action Settings

```
Settings > Editor > Code Actions > Flutter

Enable:
- Wrap widget with... suggestions
- Extract widget refactoring
- Convert to StatefulWidget
- Add key parameter suggestion
```

## Problem Recognition Patterns

Configure Cursor to recognize common Flutter issues:

### Common Flutter Errors

```
Settings > AI > Problem Recognition > Add patterns

Patterns:
- "setState() called after dispose()"
- "RenderFlex overflow"
- "Incorrect use of Parent-Data widget"
- "Missing material widgets"
```

For each pattern, configure Cursor to suggest appropriate fixes and explanations.

## Project-Level Configuration

Create a `.cursor` configuration file at your project root for team-wide settings:

```json
{
  "flutter": {
    "enableLinting": true,
    "lintRules": [
      "always_specify_types",
      "avoid_print",
      "prefer_const_constructors"
    ],
    "widgetExtraction": {
      "threshold": 5,
      "enabled": true
    },
    "stateManagement": "Provider",
    "generateDocumentation": true
  },
  "cursor": {
    "contextInclude": [
      "lib/**/*.dart",
      "test/**/*.dart",
      "pubspec.yaml"
    ],
    "contextExclude": [
      "build/**",
      ".dart_tool/**"
    ]
  }
}
```

## Keyboard Shortcuts and Commands

Configure Flutter-specific keyboard shortcuts in Cursor:

### Recommended Shortcuts

| Command | Shortcut | Description |
|---------|----------|-------------|
| Flutter Hot Reload | `Ctrl+Alt+R` | Triggers hot reload in connected device |
| Format Flutter Widget | `Ctrl+Alt+F` | Properly formats widget tree structure |
| Extract Widget | `Ctrl+Alt+W` | Extracts selected code into a new widget |
| Navigate to Definition | `F12` | Jump to widget or class definition |
| Insert Flutter Snippet | `Ctrl+Space` | Access Flutter-specific code snippets |

## Debugging Integration

Configure Cursor for optimal Flutter debugging experience:

### Debug Configuration

```
Settings > Debugging > Flutter

Options:
- Enable hot reload on save
- Track widget rebuilds
- Inspect widget tree
- Performance overlay
```

## Conclusion

By implementing these protocols and rules for Cursor AI, you'll create a more efficient Flutter development environment. These configurations help ensure consistency, reduce errors, and leverage Flutter-specific features to their fullest potential.

Remember to update these settings as your project evolves and as new Flutter or Cursor features become available.
