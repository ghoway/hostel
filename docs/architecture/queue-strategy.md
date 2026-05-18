# Queue Strategy Architecture

---

# Purpose

Defines asynchronous processing strategy.

---

# Core Principles

- Heavy operations SHOULD NOT block HTTP requests
- Long-running tasks SHOULD use queues
- User-facing requests should remain responsive

---

# Recommended Queue Usage

## Reporting

- report generation
- occupancy calculations
- export processing

---

## Notifications

- email notifications
- booking confirmations
- reminders
- future WhatsApp notifications

---

## Document Generation

- invoice PDF generation
- report exports

---

## Payment Follow-up

- post-payment processing
- analytics updates
- audit logging

---

# Performance Goals

Queue usage should:

- reduce request timeout risks
- improve scalability
- improve UX responsiveness
- reduce synchronous workload

---

# Recommended Technology

- Laravel Queues
- Database Queue Driver (initially)
- Redis Queue Driver (future scaling)
