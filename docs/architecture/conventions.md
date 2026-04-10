# Project Conventions - servi.cam

## Naming
- Tables: plural snake_case (service_requests)
- Models: singular PascalCase (ServiceRequest)
- Controllers: singular PascalCase + Controller (ServiceRequestController)
- Routes: plural kebab-case (/service-requests)
- Variables: camelCase in PHP and JS
- Constants: UPPER_SNAKE_CASE

## Database
- Always use BIGINT UNSIGNED for PKs and FKs
- All tables have created_at and updated_at except pivots
- Soft deletes only where business logic requires history
- No raw queries, always use Eloquent or Query Builder

## Code style
- PHP: PSR-12
- No comments unless explaining non-obvious logic
- Controllers thin, logic in Services or Actions
- Validation in FormRequests, never in controllers

## Git
- Branches: feature/name, fix/name, refactor/name
- Commits in english, imperative mood: "Add provider rating field"
- No commits directly to main
- PR required for merging to main

## Stack
- Backend: Laravel latest stable
- Frontend: Vue 3 + Inertia.js
- CSS: Bootstrap 5
- DB: MariaDB
- Auth: Laravel Sanctum
