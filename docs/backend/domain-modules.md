# Domain Modules

---

# Purpose

Defines backend domain boundaries and module responsibilities.

This document exists to:

- maintain architectural consistency
- avoid cross-domain spaghetti dependencies
- support scalable development
- support AI-assisted implementation

---

# Core Principles

- Each module owns its business domain
- Modules should remain cohesive
- Avoid unrelated responsibilities inside the same module
- Cross-module communication should remain explicit

---

# Recommended Domain Modules

---

# Hotel Module

## Responsibility

Handles hotel branch management.

---

## Owns

Examples:

- hotels
- hotel_images

---

## Responsibilities

- hotel profile management
- hotel operational settings
- hotel image management

---

# Room Module

## Responsibility

Handles room inventory and room types.

---

## Owns

Examples:

- room_types
- rooms
- amenities
- room_type_images

---

## Responsibilities

- room type management
- room inventory management
- room status management
- amenities management
- room availability support

---

# Booking Module

## Responsibility

Handles reservation transactions.

---

## Owns

Examples:

- bookings
- booking_items

---

## Responsibilities

- booking creation
- booking lifecycle
- booking validation
- booking cancellation
- reservation expiration
- guest reservation flow

---

# Payment Module

## Responsibility

Handles financial transactions.

---

## Owns

Examples:

- payments

---

## Responsibilities

- payment processing
- payment validation
- payment status updates
- payment gateway integration
- refund handling

---

# Front Office Module

## Responsibility

Handles operational hotel activities.

---

## Responsibilities

- walk-in bookings
- check-in process
- check-out process
- room assignment
- operational room handling

---

# Auth & Permission Module

## Responsibility

Handles authentication and authorization.

---

## Owns

Examples:

- users
- roles
- permissions

---

## Responsibilities

- authentication
- authorization
- hotel scope enforcement
- permission validation

---

# Reporting Module

## Responsibility

Handles reporting and analytics.

---

## Responsibilities

- booking reports
- occupancy reports
- revenue reports
- export generation

---

# Audit Module

## Responsibility

Handles audit logging and activity tracking.

---

## Owns

Examples:

- audit_logs

---

## Responsibilities

- activity logging
- operational audit trails
- financial audit tracking

---

# Notification Module

## Responsibility

Handles notifications and communication.

---

## Responsibilities

- email notifications
- booking confirmations
- reminders
- future WhatsApp integration

---

# Module Dependency Principles

---

# Preferred Dependency Direction

Recommended flow:

Booking
→ Payment
→ Notification

Booking
→ Room Availability

Front Office
→ Booking
→ Room

---

# Avoid

Avoid:

- circular dependencies
- deeply coupled modules
- direct cross-module DB manipulation

---

# Recommended Communication

Prefer:

- services
- actions
- events

Examples:

- BookingPaid event
- GuestCheckedIn event

---

# Queue Recommendations

Heavy module operations SHOULD use queues.

Examples:

- reporting exports
- notification sending
- PDF generation

---

# Future Scalability

Future modules MAY include:

- housekeeping
- OTA/channel manager
- loyalty program
- inventory management

These are NOT required for the initial release.

---

# Architectural Philosophy

Prefer:

- explicit module ownership
- small focused responsibilities
- maintainable boundaries

Avoid:

- god services
- mixed responsibilities
- cross-domain business leakage
