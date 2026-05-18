# Event Driven Flow

---

# Purpose

Defines business event architecture.

---

# Core Principles

- Important business actions may emit events
- Side effects should be decoupled where practical

---

# Recommended Events

Examples:

- BookingCreated
- BookingPaid
- BookingCancelled
- GuestCheckedIn
- GuestCheckedOut

---

# Recommended Listener Usage

Listeners MAY:

- send notifications
- generate invoices
- trigger analytics
- enqueue async jobs

---

# Queue Recommendations

Heavy listeners SHOULD use queues.

Examples:

- email notifications
- PDF generation
- reporting updates

---

# Event Philosophy

Prefer:

- decoupled side effects
- event-driven notifications

Avoid:

- large side-effect chains in controllers
