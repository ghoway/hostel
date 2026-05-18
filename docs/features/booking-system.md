# Booking System

---

# Purpose

The booking system manages hotel reservations made by guests or Front Office staff.

---

# Core Concepts

- Guests reserve room types, not physical rooms
- One booking may contain multiple rooms
- Physical room assignment usually occurs during check-in

---

# Booking Structure

## Booking

Master reservation transaction.

## Booking Items

Represents each room reservation.

Example:

- 2 Deluxe Rooms
- 1 Superior Room

---

# Booking Statuses

- pending
- paid
- confirmed
- checked_in
- checked_out
- cancelled
- no_show
- refunded

---

# Booking Sources

- online
- walk_in
- phone
- front_office
- travel_agent

---

# Validation Rules

- Room capacity must not exceed limits
- Booking dates must not overlap unavailable inventory
- Booking must contain at least one room
- Check-out date must be after check-in date

---

# Room Assignment

Physical rooms are preferably assigned during check-in.

---

# Expiration Rules

Online unpaid bookings may expire automatically after a configurable period.

Recommended:

- 15 minutes
- 30 minutes

---

# Edge Cases

- Multiple room booking
- Partial payment
- No-show guests
- Manual booking overrides
- Walk-in booking
