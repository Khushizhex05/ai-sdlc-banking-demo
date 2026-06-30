# Frontend (React) Instructions

## Purpose

- Define frontend engineering standards for AI-generated React code.
- Ensure consistent, maintainable, accessible, and testable UI artifacts.
- Align frontend agents with the repository's AI SDLC and the .NET backend response contract.

## Target Technology Stack

- Framework
  - React 19
  - TypeScript
  - Vite

- Routing
  - React Router

- State Management
  - Redux Toolkit

- API Communication
  - Axios

- Forms
  - React Hook Form

- Validation
  - Zod

- Styling
  - SCSS Modules

- Testing
  - Jest
  - React Testing Library

- Code Quality
  - ESLint
  - Prettier

AI agents must remain within the approved technology stack unless explicitly instructed otherwise.

## Architecture Style

- Use a feature-based architecture.
- Organize application concerns into: `features`, `pages`, `components`, `hooks`, `services`, `store`, `utils`, `assets`.
- Prefer composition and small focused modules.

## Frontend Layer Responsibilities

- Pages: compose features and represent route-level screens; orchestrate feature composition only.
- Components: own rendering and presentation. They may contain simple UI interaction logic but must not contain business workflows or API orchestration.
- Custom Hooks: encapsulate reusable UI behavior and interaction logic; expose declarative APIs for components.
- Services: own API communication, caching adapters, and external integrations; do not render UI.
- Redux Toolkit: manage shared application state and selectors for cross-feature concerns only.
- Feature folders: own feature-specific components, hooks, state, services, and tests.
- Utils: contain reusable helper functions with no UI responsibilities.

Emphasize separation of concerns and avoid mixing responsibilities across layers.

## Recommended Folder Structure

```text
src/
├── assets/
├── components/
├── features/
├── hooks/
├── pages/
├── services/
├── store/
├── styles/
├── utils/
├── App.tsx
└── main.tsx
```

## Frontend Design Principles

- Build reusable UI components with predictable APIs.
- Provide a consistent and accessible user experience across features.
- Develop mobile-first and responsive layouts.
- Separate presentation from business logic; keep components declarative.
- Ensure predictable component behavior and minimize side effects.
- Design for maintainability and incremental evolution.

## Redux Architecture Rules

- Create one slice per feature whenever practical.
- Keep selectors colocated with their feature slices.
- Avoid a monolithic global store; prefer feature-scoped slices.
- Store only shared application state in Redux; keep UI state local.
- Prefer RTK Query for server state and caching instead of storing API responses manually.
- Avoid duplicate state across Redux and component state.

## Custom Hook Guidelines

- Extract reusable logic into custom hooks to encapsulate behavior.
- Custom Hooks may orchestrate reusable UI behavior and invoke service-layer  APIs, but should not contain complex business rules.
- Keep hooks single-purpose, well-documented, and easily testable.
- Components should primarily focus on rendering and composition.
- Avoid deeply nested or interdependent hooks that create tight coupling.

## API Response Handling

- Consume the standardized backend response contract for every API interaction (success/data/error).
- Explicitly handle loading, empty, success, and error states for each request.
- Map backend error codes to user-friendly messages; do not expose raw backend exception details.
- Centralize error mapping and retry logic in the service layer or adapters.

## Responsive Design Guidelines

- Design mobile-first layouts and scale up for larger viewports.
- Use flexible grid systems and responsive spacing tokens.
- Define and use consistent breakpoints and responsive typography.
- Build adaptive components that adjust layout and behavior by viewport.

## AI Restrictions

- AI agents must not introduce additional frameworks, UI libraries, CSS frameworks, state management libraries, or architectural patterns unless explicitly instructed.
- Forbidden examples (do not add): Tailwind CSS, Bootstrap, Material UI, Ant Design, Chakra UI, Zustand, MobX, Recoil.

## React Best Practices

- Prefer controlled components for forms where possible.
- Lift state only when necessary; avoid unnecessary prop drilling.
- Prefer composition over inheritance; keep single-responsibility components.
- Use `React.memo` only when measurable benefits exist; avoid premature memoization.
- Use `useMemo` and `useCallback` only when they prevent proven performance issues.
- Avoid unnecessary re-renders by keeping props stable and using keys correctly.

## Design System Guidelines

- Build and maintain a small set of reusable UI primitives: Button, Input, Card, Modal, Table, Dialog, Loader.
- Maintain consistent spacing, typography, colors, and component behavior across the app.
- Reuse existing components before creating new ones; avoid duplicate UI implementations.
- Document component contracts and provide examples in shared story or docs when possible.

## Project Structure Rules

- Keep features self-contained with local components, styles, and tests.
- Centralize global concerns: routing, store, API services, and shared UI components.
- Co-locate component tests and styling with component source files.
- Keep import paths predictable and avoid deep relative chains.

## Component Design Standards

- Prefer functional components and hooks.
- Keep components small, single-responsibility, and reusable.
- Prefer composition over inheritance; expose clear props-driven APIs.
- Separate presentation from business logic; move orchestration into hooks or services.
- Avoid deeply nested hierarchies and reduce prop drilling using context or local stores when necessary.

## State Management Rules

- Use local component state for UI-only concerns.
- Use Redux Toolkit for shared application state and derived selectors.
- Keep server state in caching layers (e.g., RTK Query) or dedicated services, not in Redux unless required.
- Avoid global state for transient UI details.

## API Integration Rules

- Route all API calls through a dedicated `services/api` layer using Axios.
- Never call APIs directly from UI components; use hooks or service adapters instead.
- Follow the backend response contract (unified success/error schema) consistently.
- Handle loading, empty, success, and error states explicitly in UI flows.

## Routing Guidelines

- Keep route definitions centralized and typed.
- Protect authenticated routes with guards and role checks at the routing layer.
- Use lazy loading for route-based code-splitting.

## Form Handling Rules

- Use React Hook Form for form state and submission.
- Use Zod schemas for validation and typing; derive TypeScript types from schemas where possible.
- Keep validation rules reusable and colocated with form definitions.

## Styling Guidelines

- Use SCSS Modules for component-scoped styles.
- Prefer utility classes and variables for shared design tokens.
- Avoid inline styles except for dynamic runtime values that cannot be expressed in CSS.
- Build a small library of reusable UI primitives (Button, Input, Modal) with consistent theming.

## Performance Guidelines

- Prevent unnecessary re-renders; use React.memo and selective memoization judiciously.
- Use lazy loading for large modules and images.
- Optimize expensive computations with `useMemo` and `useCallback` only when proven needed.
- Measure before optimizing; prefer readable code unless optimization is justified.

## Accessibility Guidelines

- Use semantic HTML and ARIA attributes where necessary.
- Ensure keyboard accessibility for interactive elements.
- Associate labels with form controls and provide descriptive alt text for images.
- Maintain sufficient color contrast and test with common screen-reader flows.

## Error Handling Strategy

- Surface user-friendly error messages and actionable steps.
- Do not expose backend stack traces or internal error details to users.
- Provide graceful fallback UI for failed loads and partial failures.

## Testing Expectations

- Write unit tests for components, hooks, and utilities using Jest and React Testing Library.
- Test user interactions and critical flows (form submissions, navigation, API error handling).
- Mock network calls using test doubles; prefer integration tests for end-to-end validation.
- Keep tests fast, deterministic, and maintainable.

## AI Behavior Rules

- Do not over-engineer component hierarchies or introduce abstractions prematurely.
- Prefer the simplest working solution that is readable and maintainable.
- Keep business logic out of UI components; place it in services, hooks, or Application backends.
- Ask clarifying questions when UI requirements are missing or ambiguous.
- Maintain consistent code quality with linting and formatting.

## Code Review Checklist

- Are components small, focused, and reusable?
- Is business logic separated from presentation?
- Are accessibility considerations addressed?
- Are API calls routed through service layer and handled for loading/error states?
- Are state management decisions justified and minimal?
- Are styles modular and consistent with design tokens?
- Are tests included and do they cover critical behavior?
- Does the code follow ESLint and Prettier configurations?

## Authentication Guidelines

- Store authentication tokens securely; prefer HttpOnly cookies when supported by the backend.
- Never store passwords, refresh tokens, or sensitive credentials in Redux or browser storage (localStorage/sessionStorage).
- Treat authentication (who you are) and authorization (what you can do) as separate concerns.
- Automatically redirect unauthenticated users to the login page and protect routes with guards.
- Gracefully handle expired sessions and token expiration with clear UX and reauthentication flows.

Example authentication flow:

```text
User Login
  ↓
Receive JWT / Session
  ↓
Store securely
  ↓
Access Protected Routes
  ↓
Refresh / Reauthenticate when required
```

## Environment Configuration

- Use `.env` files for environment-specific configuration and read values via environment variables.
- Never hardcode API URLs or secrets in source code.
- Keep development, QA, and production configuration separate and documented.
- Document required environment variables for local and CI environments.
- AI agents must never generate or embed secrets or API keys in code.

Example required variables:

```text
VITE_API_BASE_URL
VITE_APP_NAME
VITE_ENVIRONMENT
```

## Internationalization Guidelines

- Do not hardcode user-facing strings in components; use translation resources.
- Prefer translation keys over literal strings and derive TypeScript types from resource schemas when possible.
- Format dates, currencies, and numbers using locale-aware utilities.
- Design components to accept translation keys and support future multilingual requirements.
- Keep UI text externalized and version-controlled for maintainability.

Example translation keys:

```text
auth.login.title

accounts.balance

transactions.history
```

## Naming Conventions

### Components

- Use PascalCase for component filenames and exported component names.

Examples:

```text
LoginForm.tsx
TransferCard.tsx
AccountSummary.tsx
```

### Pages

- Use PascalCase ending with "Page" for route-level components.

Examples:

```text
LoginPage.tsx
DashboardPage.tsx
TransferPage.tsx
```

### Hooks

- Prefix hook files and exports with `use` (camelCase file name recommended).

Examples:

```text
useLogin.ts
useAccounts.ts
useTransfer.ts
```

### Redux

- Use feature-focused slice names and keep files descriptive.

Examples:

```text
authSlice.ts

accountSlice.ts

transactionSlice.ts
```

### Services

- Suffix service modules with `Service` and expose clear method names.

Examples:

```text
AuthService.ts

AccountService.ts

TransactionService.ts
```

### Utilities

- Use camelCase for utility filenames and keep utilities side-effect free.

Examples:

```text
formatCurrency.ts

calculateInterest.ts

dateFormatter.ts
```

Naming must remain consistent across the repository to improve discoverability and maintainability.
