# Database Schema Rules

---

# Purpose

Defines database design principles and consistency rules.

---

# Core Principles

- Prefer explicit relationships
- Avoid duplicated business logic
- Maintain multi-hotel scalability
- Keep schema normalized where practical
- Avoid premature overengineering

---

# Multi-Hotel Rules

Most operational tables SHOULD include:

- hotel_id

Examples:

- rooms
- room_types
- bookings
- payments

Avoid hardcoding single-hotel assumptions.

---

# Booking Rules

Bookings MUST support:

- multiple room reservations
- multiple booking items

DO NOT assume:

- one booking = one room

---

# Room Reservation Rules

Guests reserve:

- room types

Guests DO NOT reserve:

- physical room numbers

Physical room assignment happens operationally during check-in.

---

# Pricing Rules

Pricing SHOULD belong to:

- room types

Avoid:

- pricing per physical room

---

# Amenities Rules

Amenities belong to:

- room types

Avoid:

- amenities per physical room

---

# Images Rules

Hotels and room types SHOULD support multiple images.

Avoid:

- single image column patterns

Preferred:

- dedicated image tables

---

# Status Rules

Statuses SHOULD use controlled values.

Examples:

- booking statuses
- payment statuses
- room statuses

Avoid:

- inconsistent free-text statuses

---

# Audit Rules

Important transactional changes SHOULD be auditable.

Examples:

- booking cancellation
- payment updates
- room assignment changes

---

# Queue Rules

Heavy operations SHOULD use queues.

Examples:

- report exports
- PDF generation
- notifications

---

# Naming Conventions

## Table Names

Use plural snake_case.

Examples:

- bookings
- booking_items
- room_types

---

## Foreign Keys

Use:

- singular_id

Examples:

- hotel_id
- booking_id
- room_type_id

---

## Timestamp Columns

Use Laravel standard:

- created_at
- updated_at

Soft deletes may be used when appropriate.

---

# Performance Considerations

Use indexes for:

- hotel_id
- booking status
- payment status
- room status
- date range queries

Avoid:

- unindexed reporting queries

# Soft Delete Rules

Soft deletes should only be used for important business entities.

Recommended:

- hotels
- room_types
- rooms
- users
- bookings
- payments

Avoid soft deletes for:

- pivot tables
- cache tables
- queue tables
- logs

Business statuses should use dedicated status fields instead of deleted_at.
