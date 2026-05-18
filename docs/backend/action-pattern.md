# Action Pattern Strategy

---

# Purpose

Defines reusable business action patterns.

---

# Core Principles

- Actions perform focused operations
- Actions should be small and reusable
- Actions should avoid unrelated responsibilities

---

# Recommended Action Examples

- CreateBookingAction
- AssignRoomAction
- CalculateBookingTotalAction
- ProcessPaymentAction
- MarkRoomOccupiedAction

---

# Action Responsibilities

Actions SHOULD:

- perform a single business operation
- remain composable
- remain testable

Actions SHOULD NOT:

- orchestrate entire workflows
- contain unrelated logic

---

# Action Philosophy

Prefer:

- small explicit actions
- composable operations

Avoid:

- giant multi-purpose actions
