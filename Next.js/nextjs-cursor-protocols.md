# Protocols and Rules for Cursor AI with Next.js

## Setting Up Cursor AI for Optimal Next.js Development

Cursor AI can significantly enhance your Next.js development workflow when configured properly. This guide outlines specific configurations, rules, and best practices to optimize Cursor for Next.js projects.

## Initial Configuration

### Environment Setup

1. **Configure Next.js Project Paths**
   
   Ensure Cursor AI is aware of your Next.js project structure:
   
   ```
   Settings > AI > Project Context > Add custom paths > [path to your Next.js project]
   ```
   
   Recommended paths to include:
   - app/ or pages/ (depending on router)
   - components/
   - lib/ or utils/
   - styles/
   - public/
   - next.config.js
   - package.json
   - tsconfig.json

2. **Set JavaScript/TypeScript Analysis Integration**

   For better code intelligence:
   
   ```
   Settings > Editor > Language Features > JavaScript/TypeScript > Enable TypeScript Server integration
   ```

3. **Include Relevant Package Documentation**

   Add Next.js documentation to your project context:
   
   ```
   Settings > AI > Project Context > Add reference URLs
   ```
   
   Recommended URLs:
   - https://nextjs.org/docs
   - https://react.dev/reference/react
   - https://tailwindcss.com/docs (if using Tailwind)
   - https://vercel.com/docs (for deployment specifics)

## Cursor Command Rules for Next.js

Create custom commands in Cursor to streamline Next.js development:

### Custom Next.js Commands

1. **Create Page Component**

   Command: `/nextjs-page`
   
   Rule configuration:
   ```
   Generate a Next.js page component at {{file_path}} that:
   - Uses the appropriate router syntax (App Router or Pages Router)
   - Includes proper metadata configuration
   - Implements responsive layout structure
   - Sets up appropriate data fetching
   ```

2. **Create API Route**

   Command: `/nextjs-api`
   
   Rule configuration:
   ```
   Generate a Next.js API route at {{file_path}} that:
   - Handles appropriate HTTP methods
   - Includes request validation
   - Implements proper error handling
   - Returns correctly formatted responses
   - Includes TypeScript types
   ```

3. **Create Layout Component**

   Command: `/nextjs-layout`
   
   Rule configuration:
   ```
   Generate a Next.js layout component for {{section_name}} that:
   - Follows App Router layout pattern
   - Includes appropriate TypeScript props
   - Sets up common UI elements
   - Handles child components appropriately
   ```

4. **Generate Data Fetching**

   Command: `/nextjs-fetch`
   
   Rule configuration:
   ```
   Implement data fetching for Next.js using {{method}} approach:
   - Include proper error handling
   - Set up appropriate caching strategies
   - Type data responses
   - Handle loading and error states
   ```

## Cursor Chat Context Rules

Configure how Cursor processes Next.js-specific context for more accurate assistance:

### Project Structure Context

Enable Cursor to understand your Next.js project structure:

```
Settings > AI > Project Context > Directory Structure > Enable
```

Set specific file inclusion patterns:
```
Include: 
- app/**/*.{js,jsx,ts,tsx}
- pages/**/*.{js,jsx,ts,tsx}
- components/**/*.{js,jsx,ts,tsx}
- lib/**/*.{js,jsx,ts,tsx}
- styles/**/*.{css,scss,sass}
- public/**/*
- next.config.js
- tsconfig.json
- package.json
- middleware.ts
```

### Code Generation Context Limits

Set maximum token limits for generated Next.js code:

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

Configure input filtering rules to ensure Cursor adheres to Next.js best practices:

### Enforce Next.js Style Guide

Create a rule that ensures generated code follows Next.js style conventions:

```
Settings > AI > Code Generation > Style enforcement > Next.js
```

This will apply rules like:
- Proper routing patterns based on router type
- Consistent data fetching approaches
- Optimized image handling with next/image
- Import ordering conventions

### Router Type Consistency

Set up a rule to maintain consistency with your chosen Next.js router:

```
Settings > AI > Project Rules > Add rule > "Router Type Consistency"

Rule definition:
{
  "pattern": "router",
  "enforce": "{{preferred_router}}",
  "allowed_values": ["App Router", "Pages Router"]
}
```

## Output Transformation Rules

Configure how Cursor's output is formatted for Next.js development:

### Component Extraction Rule

Set up a rule to automatically extract large components into smaller ones:

```
Settings > AI > Code Transformation > Add rule > "Component Extraction"

Rule definition:
{
  "condition": "Component exceeds 150 lines",
  "action": "Extract subcomponents into separate files",
  "naming_convention": "{{PurposeName}}Component"
}
```

### Data Fetching Optimization Rule

Create a rule to optimize Next.js data fetching:

```
Settings > AI > Code Transformation > Add rule > "Next.js Data Fetching"

Rule definition:
{
  "patterns": [
    "Missing fetch cache options",
    "useEffect for data fetching in Server Components",
    "Missing error handling in fetch",
    "Missing type definitions for data"
  ],
  "action": "Suggest optimized implementation"
}
```

## Next.js-Specific Editor Settings

Fine-tune Cursor's editor for Next.js development:

### Code Completion Settings

```
Settings > Editor > Code Completion > Next.js

Configuration:
- Enable next/link prop completion
- Suggest next/image with required props
- Show inline documentation for Next.js components
- Auto-import from next/ packages
```

### Code Action Settings

```
Settings > Editor > Code Actions > Next.js

Enable:
- Convert to Server Component
- Convert to Client Component
- Add 'use client' directive
- Extract to new component
```

## Problem Recognition Patterns

Configure Cursor to recognize common Next.js issues:

### Common Next.js Errors

```
Settings > AI > Problem Recognition > Add patterns

Patterns:
- "Cannot find module '@/components'"
- "useState in Server Component"
- "Hydration mismatch"
- "Missing 'use client' directive"
```

For each pattern, configure Cursor to suggest appropriate fixes and explanations.

## Project-Level Configuration

Create a `.cursor` configuration file at your project root for team-wide settings:

```json
{
  "nextjs": {
    "routerType": "App Router",
    "enableLinting": true,
    "lintRules": [
      "next/no-img-element",
      "next/no-html-link-for-pages",
      "react-hooks/exhaustive-deps"
    ],
    "componentExtraction": {
      "threshold": 150,
      "enabled": true
    },
    "dataFetchingApproach": "Server Components",
    "generateDocumentation": true
  },
  "cursor": {
    "contextInclude": [
      "app/**/*.{js,jsx,ts,tsx}",
      "components/**/*.{js,jsx,ts,tsx}",
      "lib/**/*.{js,jsx,ts,tsx}",
      "next.config.js"
    ],
    "contextExclude": [
      "node_modules/**",
      ".next/**",
      "out/**"
    ]
  }
}
```

## Keyboard Shortcuts and Commands

Configure Next.js-specific keyboard shortcuts in Cursor:

### Recommended Shortcuts

| Command | Shortcut | Description |
|---------|----------|-------------|
| Next.js Dev Server | `Ctrl+Alt+N` | Starts Next.js development server |
| Format Component | `Ctrl+Alt+F` | Properly formats component structure |
| Extract Component | `Ctrl+Alt+C` | Extracts selected code into a new component |
| Toggle Client/Server | `Ctrl+Alt+U` | Toggles 'use client' directive |
| Generate Route | `Ctrl+Alt+R` | Creates new route structure based on current router |

## Debugging Integration

Configure Cursor for optimal Next.js debugging experience:

### Debug Configuration

```
Settings > Debugging > Next.js

Options:
- Enable Fast Refresh integration
- Track component re-renders
- Performance monitoring
- Route transition debugging
```

## Router-Specific Settings

Configure specific behaviors based on your Next.js router choice:

### App Router Settings

```
Settings > AI > Framework Settings > Next.js > App Router

Configuration:
- Default to Server Components
- Auto-suggest metadata exports
- Enforce route group naming conventions
- Suggest parallel routes and intercepted routes
```

### Pages Router Settings

```
Settings > AI > Framework Settings > Next.js > Pages Router

Configuration:
- Default data fetching methods
- File-based routing assistance
- API routes structure enforcement
- getStaticProps/getServerSideProps templates
```

## Code Snippet Library

Create a custom Next.js code snippet library:

```
Settings > Editor > Snippets > Next.js

Add snippets for:
- Common layout patterns
- Data fetching templates
- Metadata configurations
- Route handlers
- Server action patterns
```

## Next.js-Specific Template Files

Create template files for common Next.js patterns:

### Layout Template

```tsx
// app/[section]/layout.tsx
import { Metadata } from 'next'
import { ReactNode } from 'react'

export const metadata: Metadata = {
  title: {
    template: '%s | Site Name',
    default: 'Site Name',
  },
}

interface LayoutProps {
  children: ReactNode
}

export default function SectionLayout({ children }: LayoutProps) {
  return (
    <section className="container mx-auto px-4 py-8">
      {children}
    </section>
  )
}
```

### Server Component Template

```tsx
// app/products/[id]/page.tsx
import { notFound } from 'next/navigation'
import { Metadata } from 'next'

interface Params {
  params: { id: string }
}

export async function generateMetadata({ params }: Params): Promise<Metadata> {
  const product = await getProduct(params.id)
  
  if (!product) {
    return { title: 'Product Not Found' }
  }
  
  return {
    title: product.name,
    description: product.description,
  }
}

async function getProduct(id: string) {
  // Fetch product logic
}

export default async function ProductPage({ params }: Params) {
  const product = await getProduct(params.id)
  
  if (!product) {
    notFound()
  }
  
  return (
    <div>
      {/* Product display */}
    </div>
  )
}
```

### API Route Template

```tsx
// app/api/resource/route.ts
import { NextRequest, NextResponse } from 'next/server'

export async function GET(request: NextRequest) {
  try {
    // Fetch data logic
    const data = { /* ... */ }
    
    return NextResponse.json(data)
  } catch (error) {
    return NextResponse.json({ error: 'Failed to fetch data' }, { status: 500 })
  }
}

export async function POST(request: NextRequest) {
  try {
    const body = await request.json()
    
    // Process data logic
    
    return NextResponse.json({ success: true }, { status: 201 })
  } catch (error) {
    return NextResponse.json({ error: 'Failed to process request' }, { status: 400 })
  }
}
```

## Conclusion

By implementing these protocols and rules for Cursor AI, you'll create a more efficient Next.js development environment. These configurations help ensure consistency, reduce errors, and leverage Next.js-specific features to their fullest potential.

Remember to update these settings as your project evolves, particularly when upgrading Next.js versions, as significant changes can occur between major releases.
