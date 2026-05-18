# Pricing Strategy Design

---

# Purpose

Defines pricing structure and pricing rules.

---

# Core Principles

- Pricing belongs to room types
- Pricing should support future extensibility
- Historical bookings must preserve pricing snapshots

---

# Base Pricing

Each room type SHOULD have:

- base price

Example:

- Standard → 100000
- Deluxe → 150000

---

# Pricing Scope

Pricing is scoped by:

- hotel
- room type

Avoid:

- pricing per physical room

---

# Historical Pricing

Bookings MUST preserve historical prices.

Changing room type prices SHOULD NOT affect:

- old bookings
- invoices
- reports

---

# Future Pricing Support

Future extensibility may include:

- weekday/weekend pricing
- seasonal pricing
- promotional pricing
- special event pricing

These are NOT required for initial release.

---

# Extra Bed Pricing

Extra bed pricing SHOULD be configurable separately.

Extra bed pricing is transactional and SHOULD NOT be treated as a room amenity.

---

# Discount Rules

Discounts SHOULD preserve:

- original price
- discount amount
- final price

Avoid recalculating historical totals dynamically.

---

# Tax & Service Rules

Bookings SHOULD preserve:

- subtotal
- tax amount
- service amount
- grand total

Avoid relying only on dynamic calculations.
