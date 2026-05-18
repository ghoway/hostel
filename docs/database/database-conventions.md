# Database Conventions

---

# Purpose

Defines database implementation conventions and consistency rules.

This document exists to:

- maintain consistency
- guide future migrations
- support AI-assisted development
- avoid architectural inconsistencies

---

# Primary Key Strategy

Use:

- bigint unsigned auto increment IDs

Preferred:

- Laravel default IDs

Avoid:

- UUIDs for initial release unless explicitly required

---

# Foreign Key Strategy

Use:

- foreignId()

Examples:

- hotel_id
- booking_id
- room_type_id

---

---

## Naming Conventions

## Tables

Use:

- plural snake_case

Examples:

- bookings
- booking_items
- room_types

---

## Models

Use:

- singular PascalCase

Examples:

- Booking
- BookingItem
- RoomType

---

## Columns

Use:

- snake_case

Examples:

- booking_number
- room_type_id
- payment_status

---

# Timestamp Strategy

Use Laravel standard timestamps:

- created_at
- updated_at

Use:

- soft deletes selectively

---

# Timezone Strategy

Application SHOULD use:

- UTC storage in database

Application/UI layer handles timezone conversion.

Avoid storing local timezone timestamps directly.

---

# Money Strategy

Use:

- integer values for money

Examples:

- 100000 = Rp100.000

Avoid:

- float
- double

Reason:

- floating point precision issues

---

# Decimal Strategy

Decimals MAY be used only when necessary.

Examples:

- percentage values
- tax rates

Avoid decimals for:

- currency storage

---

# Status Columns

Statuses SHOULD use:

- lowercase snake_case string values

Examples:

- pending
- checked_in
- cancelled

Avoid:

- inconsistent casing
- free text statuses

---

# Enum Strategy

Prefer:

- string columns with controlled application validation

Avoid:

- database ENUM types for flexible business statuses

Reason:

- easier future modifications
- easier migrations
- less schema rigidity

---

# JSON Column Strategy

JSON columns MAY be used for:

- external gateway payloads
- metadata
- third-party responses

Examples:

- payment metadata
- Midtrans payload

Avoid:

- storing core relational business data in JSON

---

# Soft Delete Strategy

Use soft deletes selectively.

Recommended:

- hotels
- users
- room_types
- rooms
- bookings
- payments

Avoid:

- pivot tables
- logs
- cache tables

---

# Audit Strategy

Important business actions SHOULD preserve historical records.

Avoid deleting:

- bookings
- payments
- audit logs

---

# Snapshot Strategy

Transactional entities SHOULD preserve historical snapshots.

Examples:

- guest_name_snapshot
- room_price_snapshot
- room_type_name_snapshot

Reason:

- historical integrity
- reporting consistency

---

# Indexing Strategy

Indexes SHOULD exist for:

- foreign keys
- status columns
- date ranges
- transaction references
- frequently filtered columns

Examples:

- hotel_id
- booking_number
- status
- checkin_date
- checkout_date

---

# Unique Constraints

Recommended unique fields:

- booking_number
- hotel slug
- room number per hotel

---

# Room Number Rules

Room numbers SHOULD be unique per hotel.

Recommended:

- composite unique index

Example:

- hotel_id + room_number

---

# Slug Rules

Slugs SHOULD be:

- lowercase
- URL friendly
- unique where applicable

Examples:

- hotel slug
- room type slug

---

# Foreign Key Delete Rules

Recommended:

- restrictOnDelete()
- nullOnDelete()

Avoid:

- cascadeOnDelete() for transactional entities

---

# Queue-Oriented Design

Heavy reporting and operational processing SHOULD assume asynchronous execution.

Examples:

- exports
- report generation
- notifications
- invoice generation

---

# Migration Principles

- Keep migrations domain-focused
- Avoid mixing unrelated entities
- Keep migrations reversible
- Avoid destructive migrations when possible

---

# Reporting Considerations

Reporting queries SHOULD:

- use indexes
- avoid unnecessary joins
- preserve historical snapshots

Heavy reports SHOULD use:

- queues
- async processing

---

# Performance Principles

Avoid:

- N+1 queries
- unnecessary eager loading
- unindexed filtering
- large synchronous exports

Prefer:

- scoped queries
- indexed filters
- paginated results
- queued processing

---

# Future Scalability Notes

Future scaling MAY include:

- Redis queues
- caching layer
- read replicas
- advanced reporting pipelines

These are NOT required for initial release.

---

# Development Philosophy

- Prioritize maintainability
- Prefer explicit business rules
- Avoid overengineering
- Preserve historical integrity
- Keep operational flows simple

Naming Conventions

---

# Purpose

Defines consistent naming conventions across the application.

---

# General Rules

- Use snake_case for database columns
- Use singular model names
- Use plural table names
- Use lowercase enum/status values

---

# Examples

## Tables

- bookings
- booking_items
- room_types

---

## Models

- Booking
- BookingItem
- RoomType

---

## Foreign Keys

- booking_id
- room_type_id
- hotel_id

---

## Status Values

Preferred:

- pending
- paid
- cancelled

Avoid:

- Pending
- CANCELLED
- booking_paid

---

# Boolean Naming

Use:

- is_active
- is_primary

Avoid:

- active_flag
- status_bool

---

# Pivot Tables

Use alphabetical naming where possible.

Examples:

- amenity_room_type
- permission_role
