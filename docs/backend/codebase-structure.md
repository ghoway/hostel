# Codebase Structure

---

# Purpose

Defines backend code organization and architectural structure.

This document exists to:

- maintain consistency
- avoid fat controllers
- centralize business logic
- support AI-assisted development

---

# Core Principles

- Keep controllers thin
- Centralize business logic
- Prefer explicit architecture
- Avoid duplicated logic
- Organize code by domain responsibility

---

# Recommended Structure

app/

- Actions/
- Enums/
- Events/
- Http/
- Jobs/
- Listeners/
- Models/
- Policies/
- Services/

---

# Controllers

Controllers SHOULD:

- receive requests
- validate requests
- call actions/services
- return responses

Controllers SHOULD NOT:

- contain heavy business logic
- contain large transactional workflows

---

# Models

Models SHOULD:

- define relationships
- define scopes
- define casts

Models SHOULD NOT:

- contain large operational workflows

---

# Services

Services SHOULD:

- orchestrate business processes
- coordinate actions
- manage transactional workflows

Examples:

- BookingService
- PaymentService
- CheckinService

---

# Actions

Actions SHOULD:

- perform focused business operations
- remain reusable
- remain small and explicit

Examples:

- CreateBookingAction
- AssignRoomAction
- ProcessPaymentAction

---

# Policies

Policies SHOULD:

- centralize authorization logic
- enforce hotel scope
- enforce permission checks

---

# Events & Listeners

Events SHOULD represent:

- important business events

Examples:

- BookingPaid
- GuestCheckedIn
- BookingCancelled

Listeners SHOULD:

- trigger notifications
- trigger async operations
- trigger analytics updates

---

# Jobs

Jobs SHOULD handle:

- asynchronous processing
- heavy operations
- exports
- notifications
- PDF generation

---

# Architectural Philosophy

Prefer:

- explicit business flows
- readable architecture
- pragmatic Laravel patterns

Avoid:

- unnecessary abstractions
- premature microservice patterns
- overengineered repository layers
