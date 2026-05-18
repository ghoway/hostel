# Multi-Hotel Scope Architecture

---

# Purpose

Defines multi-hotel data isolation and operational scope.

---

# Core Principles

- The system supports multiple hotel branches
- Most operational entities are scoped by hotel_id
- Users may only access authorized hotels

---

# Hotel Scoped Entities

Examples:

- rooms
- room_types
- bookings
- payments
- reports
- staff

---

# Super Administrator Scope

Super Administrators may access:

- all hotels
- all reports
- all operational data

---

# Staff Scope

Hotel staff should only access:

- their assigned hotel
- related operational data

---

# Development Rules

Queries SHOULD always consider hotel scope when applicable.

Avoid:

- unscoped queries
- cross-hotel data leakage
