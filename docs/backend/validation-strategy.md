# Validation Strategy

---

# Purpose

Defines validation architecture.

---

# Core Principles

- Validation should be centralized
- Avoid duplicated validation logic
- Business rules should remain consistent

---

# Recommended Validation Approach

Use:

- Laravel Form Requests

Examples:

- StoreBookingRequest
- CheckinRequest
- CheckoutRequest

---

# Validation Scope

Validation SHOULD include:

- request structure
- required fields
- basic business constraints

Complex business workflows SHOULD remain in:

- services
- actions

---

# Avoid

Avoid:

- validation inside controllers
- duplicated validation rules
