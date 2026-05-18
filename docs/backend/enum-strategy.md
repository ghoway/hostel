# Enum Strategy

---

# Purpose

Defines status and enum management strategy.

---

# Core Principles

- Business statuses should be centralized
- Avoid magic strings across the codebase

---

# Recommended Enum Usage

Examples:

- BookingStatus
- PaymentStatus
- RoomStatus
- BookingSource

---

# Recommended Status Values

## Booking Status

- pending
- paid
- confirmed
- checked_in
- checked_out
- cancelled
- no_show
- refunded

---

## Payment Status

- pending
- paid
- failed
- expired
- refunded

---

## Room Status

- available
- occupied
- reserved
- dirty
- cleaning
- maintenance
- out_of_order

---

# Enum Philosophy

Prefer:

- centralized enum definitions

Avoid:

- duplicated hardcoded strings
