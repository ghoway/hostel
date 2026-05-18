# Migration Planning

---

# Purpose

Defines migration order and database initialization strategy.

This document exists to:

- maintain schema consistency
- avoid foreign key issues
- simplify future migrations
- guide AI-assisted development

---

# Core Principles

- Create foundational tables first
- Create transactional tables later
- Create pivot tables after parent entities
- Avoid circular foreign key dependencies
- Prefer nullable foreign keys when operationally required

---

# Recommended Migration Order

## Phase 1 — Foundation Tables

### hotels

Represents hotel branches.

---

### users

Represents:

- guests
- staff
- administrators

Depends on:

- hotels

---

### permissions tables

Provided by:

- spatie/laravel-permission

Includes:

- roles
- permissions
- model_has_roles
- model_has_permissions
- role_has_permissions

---

# Phase 2 — Room Domain

### amenities

Independent master table.

---

### room_types

Depends on:

- hotels

---

### rooms

Depends on:

- hotels
- room_types

---

### room_type_images

Depends on:

- room_types

---

### hotel_images

Depends on:

- hotels

---

### amenity_room_type

Pivot table.

Depends on:

- amenities
- room_types

---

# Phase 3 — Booking Domain

### bookings

Depends on:

- hotels
- users

---

### booking_items

Depends on:

- bookings
- room_types
- rooms (nullable)

---

### payments

Depends on:

- bookings

---

# Phase 4 — Audit & Operational

### audit_logs

Depends on:

- users

---

# Foreign Key Strategy

---

# Nullable Foreign Keys

Some foreign keys SHOULD remain nullable for operational flexibility.

Examples:

- bookings.user_id
- booking_items.room_id
- users.hotel_id

---

# Deletion Strategy

Avoid cascading deletes for important transactional entities.

Examples:

- bookings
- payments
- audit logs

Historical data MUST be preserved.

---

# Recommended FK Delete Rules

## Recommended:

- restrictOnDelete()
- nullOnDelete()

Avoid:

- cascadeOnDelete() for transactional data

---

# Status Strategy

Statuses SHOULD use:

- controlled enum/string values

Avoid:

- inconsistent free text statuses

---

# Recommended Status Columns

Examples:

- booking status
- payment status
- room status

---

# JSON Columns

JSON columns MAY be used for:

- payment gateway metadata
- external provider payloads

Avoid excessive JSON usage for core relational data.

---

# Soft Delete Strategy

Soft deletes SHOULD be used selectively.

Recommended:

- hotels
- users
- room_types
- rooms
- bookings
- payments

Avoid soft deletes for:

- pivot tables
- audit logs
- queue tables

---

# Indexing Strategy

Indexes SHOULD exist for:

- hotel_id
- booking_number
- status columns
- date ranges
- room_type_id
- transaction references

---

# Seeder Strategy

---

# Initial Seeders

Recommended:

- permissions
- roles
- super administrator
- default amenities

---

# Development Seeders

Optional:

- fake hotels
- fake rooms
- fake bookings

Useful for:

- testing
- UI development
- reporting validation

---

# Migration Naming Recommendations

Examples:

- create_hotels_table
- create_room_types_table
- create_bookings_table

Avoid:

- unclear naming
- mixed domain migrations

---

# Operational Notes

Transactional tables SHOULD preserve historical snapshots.

Examples:

- guest snapshot
- pricing snapshot
- room type snapshot

Avoid relying only on live relational data for historical records.
