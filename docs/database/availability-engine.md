# Availability Engine Design

---

# Purpose

Defines room availability calculation and reservation inventory logic.

This is one of the most critical systems in the PMS.

---

# Core Principles

- Availability is calculated by room type
- Guests reserve room types, not physical rooms
- Physical rooms are assigned later operationally
- The system MUST prevent double booking

---

# Availability Scope

Availability is scoped by:

- hotel
- room type
- date range

---

# Inventory Logic

Available inventory is calculated from:

total physical rooms
MINUS
active reserved rooms
MINUS
occupied rooms
MINUS
maintenance/out_of_order rooms

---

# Active Reservation Statuses

Statuses that SHOULD affect availability:

- pending
- paid
- confirmed
- checked_in

Statuses that SHOULD NOT affect availability:

- cancelled
- checked_out
- no_show
- refunded

---

# Date Overlap Rules

The system MUST validate overlapping booking dates.

Example:

- existing booking:
  1 Jan → 3 Jan

Conflicting booking:

- 2 Jan → 4 Jan

---

# Check-in / Check-out Logic

Recommended rule:

- check-out date is exclusive

Example:

- Guest A:
  1 Jan → 3 Jan

- Guest B:
  3 Jan → 5 Jan

This SHOULD be allowed.

---

# Physical Room Assignment

Availability calculation SHOULD NOT depend on physical room assignment.

Availability should primarily use:

- room type inventory

---

# Maintenance Rooms

Rooms marked:

- maintenance
- out_of_order

SHOULD reduce available inventory.

---

# Expired Booking Handling

Expired unpaid bookings SHOULD:

- automatically release reserved inventory

---

# Concurrency Considerations

Availability validation MUST consider:

- race conditions
- simultaneous bookings

Future improvements may include:

- temporary inventory locking
- reservation hold system
- database transactions

---

# Performance Recommendations

Heavy availability calculations SHOULD:

- use indexed queries
- avoid N+1 queries
- use caching carefully

Avoid:

- expensive full-table scans
