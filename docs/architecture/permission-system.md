# Permission System Architecture

---

# Purpose

Defines authorization and permission architecture.

---

# Core Principles

- Authorization must be permission-based
- Business logic MUST NOT depend on hardcoded role names
- Roles are configurable labels/groups
- Permissions define actual capabilities

---

# Recommended Approach

DO:

- use permissions for authorization checks
- scope permissions by hotel when necessary

DO NOT:

- hardcode role names
- use role names as business rules

---

# Example Permissions

- booking.create
- booking.checkin
- booking.checkout
- room.manage
- hotel.manage
- report.view
- user.manage

---

# Hotel Scope

Users may only access resources belonging to their assigned hotel.

Super Administrators may access all hotels.

---

# Recommended Authorization Pattern

Preferred:

- permission checks
- policies
- scoped queries

Avoid:

- direct role comparisons

Bad Example:

- hasRole('admin')

Preferred Example:

- can('booking.checkin')
