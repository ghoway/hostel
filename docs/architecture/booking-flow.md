# Booking Flow Architecture

---

# Purpose

Defines the reservation lifecycle and operational booking flow.

---

# Core Principles

- Guests reserve room types, not physical rooms
- One booking may contain multiple rooms
- Physical room assignment is preferably handled during check-in
- Availability is calculated based on room type inventory

---

# Online Booking Flow

1. Guest searches room availability
2. Guest selects room types
3. Guest creates booking
4. System creates booking items
5. System calculates pricing
6. Guest proceeds to payment
7. Payment gateway callback updates payment status
8. Booking becomes confirmed/paid
9. Confirmation notification is sent asynchronously

---

# Walk-in Booking Flow

1. Front Office creates booking
2. Room availability is validated
3. Payment may be immediate/manual
4. Booking may immediately proceed to check-in

---

# Check-in Flow

1. Booking is validated
2. Outstanding payment is checked
3. Physical room is assigned
4. Booking status becomes checked_in
5. Room status becomes occupied

---

# Check-out Flow

1. Outstanding balance is validated
2. Booking status becomes checked_out
3. Room status becomes dirty or cleaning
4. Audit logs are recorded

---

# Booking Expiration

Unpaid online bookings may expire automatically.

Recommended:

- 15 to 30 minutes

Expired bookings should release reserved inventory.

---

# Queue Recommendations

The following actions SHOULD use queues:

- email notifications
- invoice generation
- booking confirmation notifications
- analytics updates
