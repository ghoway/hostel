# Policy Strategy

---

# Purpose

Defines authorization and access control strategy.

---

# Core Principles

- Authorization should use Policies
- Authorization should use permissions
- Hotel scope must be enforced

---

# Recommended Policy Targets

Examples:

- BookingPolicy
- RoomPolicy
- PaymentPolicy
- UserPolicy

---

# Authorization Rules

Policies SHOULD validate:

- permissions
- hotel ownership/scope
- operational access

---

# Recommended Checks

Examples:

- booking belongs to same hotel
- room belongs to same hotel
- user has required permission

---

# Avoid

Avoid:

- direct role checks
- scattered authorization logic
