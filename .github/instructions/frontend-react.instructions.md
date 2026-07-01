# Frontend (React) Instructions

---

# Purpose

This document defines the frontend development standards for all AI-generated React code.

Its objectives are to:

- Maintain a consistent project structure.
- Generate production-ready React applications.
- Ensure scalability and maintainability.
- Promote reusable components.
- Follow API-first development.
- Keep business logic separate from UI.
- Generate code that is testable and strongly typed.

AI agents must follow these instructions unless explicitly overridden by the user.

---

# Target Technology Stack

## Framework

- React 19
- TypeScript

## UI

- Material UI (MUI)

## State Management

- Redux Toolkit

## Routing

- React Router

## API Communication

- Axios

## Forms

- React Hook Form

## Validation

- Zod

## Testing

- Jest
- React Testing Library

## Localization

- i18next

Do not introduce additional frameworks unless explicitly requested.

---

# Output Contract

The Frontend Agent should generate only the files required for the requested feature.

Typical outputs include:

- Pages
- Components
- Hooks
- Redux Slice
- API Service
- Types
- Validation Schema
- Tests
- Route updates

Do NOT generate:

- Backend code
- Database code
- API implementations
- Infrastructure
- CI/CD
- Docker
- Kubernetes
- Unused helper classes

Generate minimal but production-ready code.

---

# Project Structure

Use the following project structure.

```
src/
│
├── api/
│
├── assets/
│
├── components/
│
├── config/
│
├── constants/
│
├── features/
│
├── hooks/
│
├── layouts/
│
├── pages/
│
├── routes/
│
├── services/
│
├── store/
│
├── styles/
│
├── theme/
│
├── types/
│
├── utils/
│
└── tests/
```

Do not create new root folders without user approval.

---

# Folder Responsibilities

## api/

Shared axios configuration.

Contains:

- axios instance
- interceptors

No business logic.

---

## assets/

Contains:

- images
- icons
- fonts
- svg
- illustrations

No components.

---

## components/

Reusable UI components shared across features.

Examples:

- Button
- Header
- Footer
- Table
- Dialog
- Loader
- Card

Keep components generic.

---

## config/

Application configuration.

Examples:

- Environment configuration
- Constants
- App configuration

---

## constants/

Application constants.

Examples:

- Routes
- API URLs
- Regex
- Messages

Avoid magic strings.

---

## features/

Feature-specific implementation.

Every feature owns its own components, services, hooks and tests.

---

## hooks/

Reusable custom hooks.

Examples:

- useAuth
- useDebounce
- usePagination

Business logic should live here when reusable.

---

## layouts/

Application layouts.

Examples:

- AuthLayout
- DashboardLayout

---

## pages/

Route-level components.

Pages orchestrate feature components.

Pages should contain minimal logic.

---

## routes/

React Router configuration.

Contains:

- Protected Routes
- Public Routes
- Route definitions

---

## services/

API communication.

Contains:

- API calls
- Service wrappers

Never call Axios directly inside components.

---

## store/

Redux Toolkit configuration.

Contains:

- store.ts
- root reducer
- slices

---

## styles/

Global styles.

Avoid feature-specific styling here.

---

## theme/

Material UI theme.

Contains:

- palette
- typography
- spacing
- breakpoints

---

## types/

Shared interfaces.

Examples:

- DTOs
- API Models
- Enums
- Response Types

---

## utils/

Pure utility functions.

Examples:

- formatDate()
- currencyFormatter()
- validators()

Utilities should have no side effects.

---

## tests/

Shared testing utilities.

Contains:

- test wrappers
- mock providers
- helpers

---

# Feature Folder Structure

Every feature should follow this structure.

```
features/

login/

    components/

    hooks/

    pages/

    services/

    store/

    types/

    validation/

    tests/
```

Only create folders required by the feature.

Avoid empty folders.

---

# Architecture Rules

Follow Feature-Based Architecture.

Business Flow

```
Page

↓

Component

↓

Hook

↓

Service

↓

Axios

↓

Backend API
```

Rules

- Pages orchestrate features.
- Components display UI.
- Hooks contain reusable UI logic.
- Services communicate with APIs.
- Redux stores shared application state.
- Components must never call Axios directly.
- Business logic must never be embedded inside JSX.
- Keep UI and business logic separated.

---

# React Standards

Use only Functional Components.

Never use Class Components.

Prefer named exports unless project conventions specify otherwise.

Each file should contain a single component.

Keep components focused on one responsibility.

Extract repeated logic into reusable hooks.

Avoid deeply nested JSX.

Prefer composition over inheritance.

Prefer reusable components over duplicated code.

Pages should assemble components instead of implementing business logic.

Keep components approximately under 200–250 lines.

Avoid unnecessary prop drilling.

Use hooks instead of helper classes.

Prefer controlled forms.

Avoid unnecessary useEffect calls.

Only use useMemo and useCallback when there is measurable benefit.

Do not optimize prematurely.

---

# TypeScript Standards

Strict mode is mandatory.

Never use:

- any
- Function
- Object

Avoid:

- unknown (unless required)
- type assertions (`as`)
- ts-ignore
- ts-expect-error

Always define:

- Component Props
- API Request Models
- API Response Models
- Hook Return Types
- Service Return Types

Prefer:

Interfaces

```ts
interface LoginRequest {
    email: string;
    password: string;
}
```

Use type aliases for:

- unions
- utility types
- mapped types

Example

```ts
type Status = "success" | "failure";
```

Always provide explicit return types for exported functions.

Use readonly where appropriate.

Avoid nullable values unless required.

Prefer optional properties over null.

Never disable strict TypeScript settings.

Use enums only when shared across multiple modules.

Prefer constants for UI values.

Keep interfaces close to the feature that owns them.

Do not duplicate API models.

Reuse existing types whenever possible.

---

# Material UI Standards

- Use Material UI v5+ only.
- Do not mix with Bootstrap or Tailwind.
- Use sx prop for styling instead of CSS files.
- Use theme-based spacing only.
- Prefer MUI components over native HTML where applicable.

Allowed MUI Components:
- Box
- Grid
- Stack
- Typography
- Button
- TextField
- Paper
- Card
- Dialog
- Snackbar
- AppBar
- Toolbar

Rules:
- Avoid inline styles (style={{}}).
- Avoid creating custom UI components when MUI already provides one.
- Always use responsive design using MUI breakpoints.

---

# Responsive Breakpoints

Use MUI theme breakpoints only:

- xs (0px)
- sm (600px)
- md (900px)
- lg (1200px)
- xl (1536px)

Rules:
- Do not use raw media queries.
- Always use theme.breakpoints.
- Ensure all pages are mobile-first.

---

# React Router Standards

- Use React Router v6+
- Define all routes in /routes folder.

Rules:
- Separate public and protected routes.
- Use layout-based routing.
- Lazy load pages when possible.

Example:

```ts
const LoginPage = lazy(() => import("../pages/LoginPage"));
```

- Protect routes using wrapper components.
- Do not define routes inside components.

---

# Redux Toolkit Standards

Rules:
- One slice per feature.
- Keep global state minimal.
- Do not store derived state.

Store Template:

```ts
import { configureStore } from "@reduxjs/toolkit";

export const store = configureStore({
  reducer: {},
});

export type RootState = ReturnType<typeof store.getState>;
export type AppDispatch = typeof store.dispatch;
```

Slice Template:

```ts
import { createSlice } from "@reduxjs/toolkit";

interface ExampleState {
  loading: boolean;
}

const initialState: ExampleState = {
  loading: false,
};

const exampleSlice = createSlice({
  name: "example",
  initialState,
  reducers: {
    setLoading: (state, action) => {
      state.loading = action.payload;
    },
  },
});

export const { setLoading } = exampleSlice.actions;
export default exampleSlice.reducer;
```

Rules:
- Never mutate state outside slices.
- Use Redux only for shared state.
- Do not store UI-only state in Redux.

---

# Axios Standards

Rules:
- Single axios instance only.
- All API calls must go through services layer.

Axios Instance:

```ts
import axios from "axios";

export const api = axios.create({
  baseURL: process.env.REACT_APP_API_BASE_URL,
  headers: {
    "Content-Type": "application/json",
  },
});
```

Interceptors:

```ts
api.interceptors.request.use((config) => {
  const token = localStorage.getItem("token");
  if (token) config.headers.Authorization = `Bearer ${token}`;
  return config;
});
```

Rules:
- Never call axios directly inside components.
- Always use service layer.

---

# Service Template

```ts
import { api } from "../api/axios";

export const loginService = async (data: LoginRequest) => {
  const response = await api.post("/auth/login", data);
  return response.data;
};
```

Rules:
- Services only handle API communication.
- No UI logic inside services.

---

# Hook Template

```ts
import { useState } from "react";
import { loginService } from "../services/loginService";

export const useLogin = () => {
  const [loading, setLoading] = useState(false);

  const login = async (data: any) => {
    setLoading(true);
    try {
      return await loginService(data);
    } finally {
      setLoading(false);
    }
  };

  return { login, loading };
};
```

Rules:
- Hooks handle reusable logic.
- Do not include JSX inside hooks.

---

# Page Template

```ts
export const LoginPage = () => {
  return (
    <div>
      <LoginForm />
    </div>
  );
};
```

Rules:
- Pages are orchestration layer only.
- No API calls in pages.
- No business logic in pages.

---

# Component Template

```ts
interface Props {
  title: string;
}

export const SampleComponent = ({ title }: Props) => {
  return (
    <div>
      {title}
    </div>
  );
};
```

Rules:
- One component per file.
- Keep components reusable.
- Avoid heavy logic inside components.

---

# API Flow

Standard flow:

UI → Hook → Service → Axios → Backend

Rules:
- Never break this flow.
- Never call backend directly from UI.

---

# UI Theme Rules

- Use centralized theme configuration.
- Do not hardcode colors.
- Use theme.palette only.

Rules:
- All spacing must use theme.spacing.
- All fonts must use theme.typography.
- Maintain consistent design system.

---

# i18n Rules

- Use i18next only if multilingual support is required.
- Do not hardcode reusable strings.
- Store translations in /locales folder.

---

# Testing Standards

Frameworks:
- Jest
- React Testing Library

Rules:
- Test user behavior, not implementation.
- Mock API calls.
- Avoid snapshot testing unless required.

Component Test Example:

```ts
import { render, screen } from "@testing-library/react";
import { LoginPage } from "../LoginPage";

test("renders login page", () => {
  render(<LoginPage />);
  expect(screen.getByText(/login/i)).toBeInTheDocument();
});
```

Service Test Example:

```ts
import { loginService } from "../loginService";

test("login service returns response", async () => {
  const data = await loginService({ email: "test@test.com", password: "123" });
  expect(data).toBeDefined();
});
```

Rules:
- Minimum 1 test per feature.
- Cover happy path + failure path.

---

# File Naming Rules

- Use PascalCase for components: LoginPage.tsx
- Use camelCase for hooks: useLogin.ts
- Use kebab-case for folders: login-feature/
- Use descriptive names only.

---

# AI Restrictions

- Do not use any type.
- Do not generate unused code.
- Do not duplicate components.
- Do not create multiple implementations of same logic.
- Do not bypass architecture rules.
- Do not write backend logic.
- Do not hardcode API URLs.
- Do not skip service layer.
- Do not break folder structure.
- Always prefer reusable components.

---

# Code Review Checklist

Before finalizing code:

- Uses TypeScript strictly
- No `any` usage
- Uses Material UI properly
- Follows API → Service → Hook → UI flow
- No direct API calls in components
- Redux used only when needed
- Responsive design implemented
- Proper folder structure followed
- Reusable components used
- Tests included
- No duplicated logic
- Clean separation of concerns

---
# END OF FRONTEND INSTRUCTION FILE