# Next.js Prompt Engineering Guide

## Introduction to Prompt Engineering for Next.js

Effective prompt engineering can significantly enhance your Next.js development workflow when using AI tools like Cursor. This guide provides best practices for crafting prompts specifically tailored for Next.js development, accounting for its unique features like server components, routing, and data fetching strategies.

## Core Principles for Next.js-Specific Prompts

### 1. Be Specific About Component Type

Next.js has different component types with distinct capabilities:

**Basic prompt:**
```
Create a page component
```

**Improved prompt:**
```
Create a Next.js server component for a product details page (/app/products/[id]/page.tsx) that fetches data from a REST API. Include error handling for missing products, loading states, and metadata for SEO. The component should use server-side data fetching with proper caching strategies and implement incremental static regeneration with a 1-hour revalidation period.
```

### 2. Include Rendering Strategy Context

Specify your rendering approach for better contextual responses:

**Basic prompt:**
```
Generate code for a blog post page
```

**Improved prompt:**
```
Generate a Next.js blog post page using static generation (SSG) with getStaticProps and getStaticPaths. The page should dynamically generate routes based on markdown files in the content directory, include rich metadata, implement a responsive layout, and use Next.js Image component for optimized images. Include TypeScript interfaces for the blog post data.
```

### 3. Define Routing Requirements

Next.js's routing system requires specific considerations:

**Basic prompt:**
```
Create a navigation component
```

**Improved prompt:**
```
Create a Next.js navigation component using App Router that highlights the active route. The navigation should include nested routes for the dashboard section, implement mobile responsiveness with a hamburger menu, and use Next.js Link components for client-side navigation. Add prefetching for important routes and include TypeScript for route typing.
```

### 4. Specify Data Fetching Strategy

Clearly indicate which Next.js data fetching method you're using:

**Basic prompt:**
```
Write code to fetch data
```

**Improved prompt:**
```
Create a Next.js data fetching implementation using React Server Components and the fetch API with proper caching directives. Implement error boundaries for fetch failures, loading states, and type-safe data handling. The data should be fetched from our API endpoint at /api/users with pagination support.
```

### 5. Describe Desired Styling Approach

Next.js supports multiple styling options - be explicit:

**Basic prompt:**
```
Style a component
```

**Improved prompt:**
```
Create a styled hero section using CSS Modules in Next.js. The component should have a full-width background image with text overlay, responsive behavior for mobile devices, and animation for text entrance. Implement the styles following our BEM naming convention and include dark mode support using CSS variables.
```

## Prompt Templates for Common Next.js Tasks

### Creating a New Page

```
Create a Next.js page located at [file path] that serves as [purpose of page].

Technical specifications:
- Rendering strategy: [SSG/SSR/ISR/Client-side]
- Router type: [App Router/Pages Router]
- Data fetching: [Server Components/getServerSideProps/SWR/React Query]
- TypeScript: [Yes/No]

The page should include:
- [List of UI components]
- [Interaction behaviors]
- [API calls if applicable]
- [SEO metadata]

Style guide:
- [Styling approach: CSS Modules/Tailwind/styled-components/etc.]
- [Color scheme references]
- [Typography specifications]
```

### Implementing API Routes

```
Create a Next.js API route at [file path] that [describe purpose].

Technical specifications:
- HTTP methods: [GET/POST/PUT/DELETE]
- Authentication: [Required/Not required]
- Request validation: [Zod/Joi/Manual validation]
- Response format: [JSON structure]

The API should:
- [Handle specific data operations]
- [Include error handling for cases: X, Y, Z]
- [Implement rate limiting if applicable]
- [Handle CORS if applicable]

Include appropriate TypeScript types for request and response.
```

### Setting Up Data Fetching

```
Implement data fetching for a Next.js [page/component] that retrieves [data description].

Requirements:
- Fetching method: [Server Components/getServerSideProps/getStaticProps/SWR/React Query]
- Caching strategy: [stale-while-revalidate/no-store/force-cache/specified duration]
- Error handling: [Specific approach]
- Loading states: [How to handle loading]

Data source:
- [API endpoint details]
- [Required parameters]
- [Authentication details if needed]

Provide appropriate TypeScript interfaces for the data structure.
```

## Best Practices for Refining Generated Next.js Code

1. **Request Component Extraction**: Ask AI to extract reusable components from complex pages

2. **Ask for Test Coverage**: Request tests for generated components
   ```
   Add Jest and React Testing Library tests for the above page component that verify proper data fetching, rendering, and user interactions
   ```

3. **Request Performance Considerations**:
   ```
   Refactor this code to optimize for performance by implementing proper image optimization, component lazy loading, and minimizing client-side JavaScript
   ```

4. **Prompt for Documentation**:
   ```
   Add JSDoc comments to all component props, functions, and especially the data fetching mechanisms
   ```

5. **Ask for Alternative Approaches**:
   ```
   What alternative Next.js data fetching methods could achieve the same result but with better [performance/user experience/maintainability]?
   ```

## Next.js-Specific Prompt Do's and Don'ts

### Do's:
- Specify Next.js version when version-specific features are needed
- Clarify whether you're using Pages Router or App Router
- Indicate client vs. server component requirements when using App Router
- Include details about your data sources and API endpoints
- Mention your preferred styling approach (CSS Modules, Tailwind, etc.)

### Don'ts:
- Don't mix App Router and Pages Router patterns in the same prompt
- Avoid requesting server-side features in client components
- Don't omit caching requirements for data fetching
- Avoid vague rendering strategy requests ("make it fast")
- Don't request deprecated Next.js APIs without acknowledging the deprecation

## Advanced Prompt Strategies

### 1. Using Iterative Refinement
Start with a basic implementation and progressively enhance it:

```
// Initial prompt
Create a basic Next.js product page that displays product details

// Follow-up prompts
1. Add metadata and structured data for SEO
2. Implement optimized image loading with next/image
3. Add incremental static regeneration with a 1-hour revalidation period
```

### 2. Context-Building for Complex Features

```
I'm building a Next.js e-commerce app with the following structure:
- App Router for routing
- Server Components for product pages
- Route handlers for API functionality
- PostgreSQL database with Prisma
- NextAuth.js for authentication

Now, help me implement the product detail page with:
1. Server component for initial rendering
2. Client components for interactive elements
3. Streaming for loading states
4. Optimized images and layout
```

### 3. Specifying Code Organization

```
Generate a Next.js feature following a modular architecture with:
- Page component at app/features/[feature]/page.tsx
- Components folder for UI elements
- Lib folder for utilities and data fetching logic
- Server actions for form submissions
- Types folder for TypeScript interfaces

Each component should be in its own file with index exports.
```

### 4. Next.js 14 App Router-Specific Prompts

```
Create a Next.js 14 dashboard layout using:

1. A root layout with:
   - Persistent navigation
   - Auth protection through middleware
   - Global error boundary

2. Nested layouts for:
   - Dashboard main area
   - Settings section
   - Analytics section

3. Implement parallel routes for:
   - Main content
   - Notifications panel (@notifications)
   - User profile modal (@profile)

Use Server Components where possible and Client Components only for interactive elements.
```

### 5. Data Fetching Strategy Prompts

```
Implement three different data fetching approaches for a user profile in Next.js:

1. Using React Server Components with fetch and proper caching:
   - Detail the fetch options for caching
   - Show error handling
   - Type the response data

2. Using SWR on the client side:
   - Show optimistic UI updates
   - Implement error handling
   - Set up revalidation

3. Using Next.js Route Handlers as an API:
   - Implement proper response structure
   - Add error handling
   - Include authentication checks

Compare the advantages of each approach in comments.
```

## Next.js-Specific Prompt Categories

### Routing and Navigation Prompts

```
Set up a Next.js App Router structure for an e-commerce site with:
- Root layout with global elements
- Product catalog at /products with filtering capabilities
- Product detail page at /products/[id] with related products
- Categorized browsing at /categories/[category]
- Search functionality with dynamic filtering
- Authentication-protected user dashboard with nested routes
- Custom 404 and error pages

Include middleware for authentication checks and TypeScript types for route params.
```

### Optimization Prompts

```
Optimize the following Next.js page for performance:

[paste code]

Focus on:
1. Converting to Server Components where appropriate
2. Adding proper image optimization with next/image
3. Implementing code splitting and lazy loading
4. Setting up appropriate caching strategies for data
5. Minimizing client-side JavaScript
```

### Deployment Configuration Prompts

```
Create deployment configuration files for a Next.js application targeting:

1. Vercel deployment:
   - vercel.json configuration
   - Environment variable setup
   - Serverless function optimization

2. Docker/Kubernetes deployment:
   - Dockerfile for production build
   - Docker Compose for local development
   - Kubernetes manifests for deployment

3. AWS Amplify deployment:
   - amplify.yml configuration
   - Build settings optimization

Include configuration for handling environment variables securely.
```

## Next.js Framework-Specific Prompts

### Next.js with Tailwind CSS

```
Create a responsive hero section for a Next.js landing page using Tailwind CSS.
The component should:
- Span full viewport width with constrainted content width
- Have a background gradient or image with proper overlay
- Include a heading, subheading, and CTA button
- Implement mobile-first responsive design with at least 3 breakpoints
- Use Tailwind's dark mode support for theme switching
- Include subtle animations for text and button entry

Provide the component as a Server Component in the App Router structure.
```

### Next.js with TypeScript

```
Convert the following JavaScript Next.js component to TypeScript with proper type safety:

[paste JavaScript component]

Include:
- Proper interface definitions for props
- Type-safe data fetching
- Path and query parameter typing
- Event handler type definitions
- Exhaustive prop validation
- Export type definitions for reuse

Ensure the conversion maintains all functionality while adding complete type coverage.
```

### Next.js with Testing

```
Create a comprehensive test suite for a Next.js checkout flow with:

1. Unit tests for:
   - Form validation functions
   - Price calculation utilities
   - State management logic

2. Component tests for:
   - Form input components
   - Payment method selection
   - Order summary display

3. Integration tests for:
   - Complete checkout flow
   - Error handling scenarios
   - Success confirmation

Use Jest and React Testing Library with proper mocking of:
- API calls
- Next.js routing
- Authentication context
```

## Conclusion

Effective prompt engineering for Next.js development requires specificity about component types, rendering strategies, routing, data fetching, and styling approaches. By following these guidelines, you can generate more accurate, useful, and maintainable Next.js code using AI assistants.

Remember to explicitly state which version of Next.js you're using and whether you're working with the App Router or Pages Router, as this fundamentally affects the code patterns and available features.
