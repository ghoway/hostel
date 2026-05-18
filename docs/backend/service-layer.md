# Service Layer Strategy

---

# Purpose

Defines service layer responsibilities.

---

# Core Principles

- Services orchestrate workflows
- Services coordinate actions
- Services centralize transactional business logic

---

# Recommended Responsibilities

Services MAY:

- coordinate multiple actions
- manage DB transactions
- coordinate external integrations
- orchestrate workflows

Services SHOULD NOT:

- directly handle HTTP concerns
- contain view rendering logic

---

# Example Services

- BookingService
- PaymentService
- RoomAvailabilityService
- CheckinService
- CheckoutService

---

# Transaction Strategy

Complex multi-step operations SHOULD use database transactions.

Examples:

- booking creation
- payment processing
- check-in workflows

---

# Service Philosophy

Prefer:

- explicit methods
- focused responsibilities

Avoid:

- giant god services
- mixed domain responsibilities
