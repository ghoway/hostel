# Payment System

---

# Purpose

Handles online and onsite hotel payments.

---

# Supported Payment Methods

- Midtrans
- Cash
- Bank Transfer
- EDC/Card

---

# Online Payment Flow

1. Guest creates booking
2. System creates payment transaction
3. Guest completes payment
4. Midtrans callback updates payment status
5. Booking status is updated

---

# Manual Payment Flow

Front Office staff may:

- receive payment
- validate payment
- update payment status manually

---

# Payment Statuses

- pending
- paid
- failed
- expired
- refunded

---

# Validation Rules

- Payment amount must match booking total
- Refunded bookings must be logged
- Manual payment actions should be auditable

# Queue Recommendations

Post-payment actions SHOULD use queues.

Examples:

- email notifications
- invoice generation
- analytics updates
