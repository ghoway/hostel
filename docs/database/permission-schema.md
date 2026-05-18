# Permission & Authorization Schema

---

# Purpose

Defines authorization schema and hotel access scope.

The system uses:

- dynamic roles
- permission-based authorization
- hotel-scoped operational access

---

# Core Principles

- Business logic MUST NOT depend on role names
- Authorization should rely on permissions
- Roles are configurable labels/groups
- Hotel operational access should be scoped

---

# Authorization Strategy

## Roles

Roles are used for:

- grouping permissions
- easier management
- operational categorization

Examples:

- Front Office
- Supervisor
- Manager
- Cashier

Role names are NOT fixed.

---

## Permissions

Permissions represent actual capabilities.

Examples:

- booking.create
- booking.checkin
- booking.checkout
- room.manage
- report.view
- user.manage

Business logic SHOULD use permission checks.

---

# Users Table Scope

Users may belong to:

- a specific hotel
  OR
- global/system level access

Example:

- Front Office user → hotel scoped
- Super Administrator → global access

---

# Recommended User Scope

## users

Recommended columns:

- hotel_id nullable

Rules:

- nullable hotel_id = global access
- specific hotel_id = hotel scoped access

---

# Spatie Permission Tables

The system uses:

- spatie/laravel-permission

Default tables:

- roles
- permissions
- model_has_roles
- model_has_permissions
- role_has_permissions

---

# Hotel Scope Considerations

The default Spatie schema does NOT handle hotel scope automatically.

Application logic MUST enforce:

- hotel data isolation
- scoped queries
- policy validation

---

# Recommended Authorization Pattern

Preferred:

- permission checks
- Laravel Policies
- scoped Eloquent queries

Avoid:

- direct role comparisons

---

# Bad Example

Avoid:

- hasRole('admin')

Because:

- role names are dynamic
- business requirements may change

---

# Preferred Example

Preferred:

- can('booking.checkin')

---

# Policy Recommendations

Authorization SHOULD use:

- Laravel Policies
- scoped resource ownership
- permission checks

Example:

- booking belongs to same hotel
- room belongs to same hotel

---

# Hotel Scope Validation

Operational users SHOULD only access:

- their assigned hotel
- related bookings
- related rooms

---

# Super Administrator Access

Super Administrators may:

- access all hotels
- manage all data
- manage users and permissions

---

# Recommended Query Scope

Queries SHOULD always consider:

- hotel_id
- user scope

Avoid:

- unscoped global queries

---

# Future Scalability

Future improvements MAY include:

- multi-hotel staff assignment
- hotel group access
- regional management
- advanced permission inheritance

These are NOT required for the initial release.
