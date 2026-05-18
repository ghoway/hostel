# Booking Schema Design

---

# Purpose

Defines booking-related database structure and business rules.

The booking system is the core transactional domain of the PMS.

---

# Core Principles

- One booking may contain multiple room reservations
- Guests reserve room types, not physical rooms
- Physical room assignment occurs operationally during check-in
- Booking data should preserve historical pricing snapshots

---

# Main Entities

## bookings

Represents the master reservation transaction.

Example:

- Booking number
- Guest information
- Hotel
- Overall totals
- Booking status

---

## booking_items

Represents each room reservation inside a booking.

Example:

- Deluxe Room x2
- Standard Room x1

Each booking item may later be assigned to a physical room.

---

# Booking Relationships

## bookings

Relationships:

- belongs to hotel
- belongs to guest/user
- has many booking_items
- has many payments

---

## booking_items

Relationships:

- belongs to booking
- belongs to room_type
- optionally belongs to assigned room

---

# Multi Room Booking

A single booking MUST support multiple booking items.

This supports:

- family bookings
- group bookings
- corporate bookings

---

# Pricing Snapshot Strategy

Booking items SHOULD preserve historical pricing data.

Examples:

- room_type_name_snapshot
- room_price_snapshot
- capacity_snapshot

This prevents historical booking corruption if room types change later.

---

# Guest Capacity Tracking

Each booking item SHOULD support:

- adult count
- child count
- infant count
- extra bed count

---

# Booking Status Lifecycle

Recommended lifecycle:

- pending
- paid
- confirmed
- checked_in
- checked_out
- cancelled
- no_show
- refunded

---

# Booking Source Tracking

Bookings SHOULD track source/channel.

Examples:

- online
- walk_in
- phone
- front_office
- travel_agent

---

# Expiration Rules

Unpaid online bookings may expire automatically.

Recommended expiration:

- 15 to 30 minutes

Expired bookings should release reserved inventory.

---

# Room Assignment Rules

Physical room assignment:

- is optional during booking
- is preferred during check-in

Assigned room must:

- belong to correct hotel
- belong to correct room type
- be available

---

# Cancellation Rules

Cancelled bookings SHOULD:

- preserve historical records
- preserve payment records
- preserve audit logs

Cancellation should use:

- booking status

Avoid deleting bookings.

---

# Audit Recommendations

Important changes SHOULD be auditable.

Examples:

- status changes
- room reassignment
- cancellation
- manual override
