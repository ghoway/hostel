# Authentication & Permission System

---

# Purpose

Handles authentication, authorization, and role management.

---

# Authentication

The system uses Laravel authentication.

---

# Authorization

Authorization is permission-based.

Business logic MUST NOT depend on hardcoded role names.

---

# Roles

Roles are dynamic and configurable.

Examples:

- Supervisor
- Manager
- Front Office
- Cashier

---

# Permissions

Examples:

- booking.create
- booking.checkin
- booking.checkout
- room.manage
- report.view
- user.manage

---

# Hotel Scope

Users may be limited to specific hotels.

Super Administrators may access all hotels.
