# Backend Architecture

---

# Purpose

Defines backend architectural principles.

---

# Core Principles

- Keep controllers thin
- Keep business logic centralized
- Avoid duplicated logic
- Prefer modular domain organization

---

# Recommended Layers

## Controllers

Handle:

- HTTP requests
- validation orchestration
- response formatting

Controllers SHOULD NOT contain heavy business logic.

---

## Services / Actions

Business logic SHOULD live inside:

- services
- actions
- domain classes

Examples:

- BookingService
- PaymentService
- RoomAvailabilityService

---

## Policies

Authorization rules SHOULD use:

- Laravel Policies
- permission checks

---

## Queues

Heavy asynchronous operations SHOULD use queues.

---

# Recommended Structure

app/

- Actions/
- Services/
- Models/
- Policies/
- Jobs/
- Events/
- Listeners/

---

# Development Principles

- Avoid overengineering
- Prefer explicit business rules
- Keep architecture consistent
- Maintain readability

# Inertia Architecture Notes

The system uses Inertia.js as the bridge between Laravel and Vue.

Routing is primarily handled by Laravel routes.

Frontend pages are rendered using:

- Inertia::render(...)

Vue pages live inside:

- resources/js/pages

This architecture intentionally avoids fully separated SPA complexity.

# Frontend Routing Rules

Do NOT introduce Vue Router unless explicitly required.

Laravel routes are the primary routing mechanism.
