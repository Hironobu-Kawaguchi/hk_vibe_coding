# Constitution: Project FusionSphere

## 1. Project Philosophy

- **Goal**: A high-performance, developer-friendly API server and web front-end, developed within a unified monorepo.
- **Core Principle**: Simplicity and explicitness over magic. Maintainability is the highest priority, and development efficiency is maximized through shared code and optimized task execution.

## 2. Tech Stack

- **Monorepo & Build System**:
  - **Package Manager**: `pnpm` (with workspaces enabled)
  - **Build System**: `Turborepo` for high-performance task execution and caching.
- **Backend**:
  - **Language**: Python 3.12
  - **Framework**: FastAPI 0.110.0
  - **Data Models**: Pydantic V2 for data validation and settings management.
  - **Package Manager**: `uv`
- **Frontend**:
  - **Language**: TypeScript 5.3
  - **Framework**: Next.js 14.1 (with App Router)
  - **UI Library**: React 18.2
  - **Data Models & Validation**:
    - **Zod**: Used for runtime validation of all external data, such as API responses and form submissions.
    - **Type Generation**: TypeScript types for API communication SHOULD be auto-generated from the backend's OpenAPI schema to ensure consistency. `openapi-typescript` is the recommended tool.
- **Database**: PostgreSQL 16
- **Cache**: Redis 7.2

## 3. Architecture

- **Overall**: A monorepo structure managed by `pnpm` workspaces. This allows for shared code between applications. All technical designs MUST adhere to the principle of **Separation of Concerns**.
- **Directory Structure**:
  - `apps/`: Contains individual, deployable applications.
    - `apps/backend/`: The FastAPI Python application.
    - `apps/frontend/`: The Next.js web application.
    - `apps/e2e-tests/`: The Playwright End-to-End test suite.
  - `packages/`: Contains shared code, libraries, or configurations used by one or more applications.
    - `packages/ui/`: Shared React components.
    - `packages/eslint-config-custom/`: Shared ESLint configuration.
    - `packages/tsconfig/`: Shared TypeScript configurations.
- **Backend Application Structure**:
    - `apps/backend/routers/`: Defines API endpoints exposed to our frontend. (The "Front of House")
    - `apps/backend/services/`: Contains core business logic. (The "Kitchen")
    - `apps/backend/clients/`: For modules that communicate with external, third-party APIs. Each external service MUST have its own dedicated client module. (The "Delivery Entrance")

## 4. Development Workflow & Commands

- **Golden Rule**: All tasks (**dev**, **build**, **test**, **lint**) **MUST** be executed from the monorepo root directory using `turbo` commands. Do not run commands from individual app directories.
- **Core Commands**:
  - `turbo dev`: Starts all applications in development mode.
  - `turbo build`: Builds all applications and packages.
  - `turbo test`: Runs unit and component tests across the entire monorepo.
  - `turbo lint`: Lints the entire codebase.
  - `turbo e2e`: Runs the end-to-end tests (requires a running application).
- **Reasoning**: Using the root `turbo` commands ensures that Turborepo's caching and task orchestration are fully utilized, maximizing development speed and consistency.

## 5. Testing Strategy

### 5.1 Unit & Component Testing
- **Backend**:
  - **Framework**: `pytest`.
  - **Location**: Tests must be placed in the `apps/backend/tests` directory.
- **Frontend**:
  - **Framework**: `Jest` with `React Testing Library`.
  - **Location**: Component tests should be co-located with the component file.

### 5.2 End-to-End (E2E) Testing
- **Framework**: **Playwright**.
- **Purpose**: To simulate real user scenarios across the entire application stack (frontend + backend).
- **Location**: A dedicated application located at `apps/e2e-tests/`.
- **Execution Policy**: E2E tests **MUST** run against a production-like build of the application. They are primarily executed in the CI/CD pipeline against a preview/staging environment after a successful deployment.

## 6. Design & Documentation

- **API Specification**: All API endpoints MUST be documented via FastAPI's auto-generated OpenAPI schema. This schema is the **Single Source of Truth** for the API contract between the frontend and backend.
- **Data Model Diagrams**: Core data models and their relationships SHOULD be documented using class diagrams (Mermaid syntax recommended) and stored in the `/docs` directory.

## 7. Prohibited Practices (Negative Constraints)

- **General**:
  - Do not commit secrets or API keys to the repository. Use environment variables managed by Pydantic's settings management.
- **Frontend**:
  - Do not use `jQuery`.
  - Do not use default exports (`export default`). Use named exports only to improve discoverability and consistency.