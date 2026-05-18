# Hotel Reservation & Property Management System (PMS)

## Software Requirements Specification (SRS)

---

# 1. Project Overview

## 1.1 Purpose

This project is a web-based Hotel Reservation and Property Management System (PMS).

The system supports:

- Multi-hotel management
- Online guest reservations
- Front office operations
- Room management
- Payment processing
- Hotel administration

This system is NOT a public SaaS platform.

The system is intended for internal use by a single hotel business entity operating multiple hotel branches.

---

# 2. Technology Stack

## Backend

- Laravel
- Inertia.js
- PostgreSQL

## Frontend

- Vue 3
- TypeScript
- Tailwind CSS

## Additional Services

- Midtrans Payment Gateway
- Queue System
- Email Notifications

# Frontend Architecture

The application uses Laravel + Inertia.js + Vue architecture.

This is NOT a separated frontend/backend SPA architecture.

Laravel handles:

- routing
- controllers
- authorization
- session authentication
- backend business logic

Vue is used as the frontend rendering layer through Inertia.js.

The frontend should follow Inertia.js patterns instead of traditional REST SPA patterns.

Avoid:

- unnecessary API abstraction
- duplicate frontend routing
- redundant client-side state management

---

# 3. Core Business Concepts

## 3.1 Multi-Hotel Architecture

The system supports multiple hotel branches.

Example:

- Hotel Jakarta
- Hotel Bandung
- Hotel Bali

All hotels are managed inside one centralized system.

Most operational entities are scoped by `hotel_id`.

---

## 3.2 Room Type Based Reservation

Guests reserve room types, NOT physical room numbers.

Example room types:

- Standard
- Deluxe
- Superior

Physical room assignment is typically handled during check-in by Front Office staff.

---

## 3.3 Physical Rooms

Physical rooms belong to room types.

Example:

- Deluxe Room
    - Room 201
    - Room 202
    - Room 203

---

# 4. User Roles

## 4.1 Guest

Guest users can:

- Register/login
- Search rooms
- Create bookings
- Make payments
- View booking history
- Cancel bookings (based on policy)

---

## 4.2 Front Office Staff

Front Office staff can:

- Create walk-in bookings
- Create manual bookings
- Assign rooms
- Process check-in
- Process check-out
- Receive manual payments
- View room availability

---

## 4.3 Administrator

Administrators can:

- Manage hotels
- Manage room types
- Manage rooms
- Manage amenities
- Manage pricing
- Manage bookings
- Manage reports
- Manage users

---

## 4.4 Super Administrator

Super Administrators have full access across all hotels.

---

# 5. Authorization System

The system uses permission-based authorization.

Role names are dynamic and configurable.

Business logic MUST NOT depend on hardcoded role names.

Example role names:

- Supervisor
- Manager
- Front Office
- Cashier

Authorization should rely on permissions instead.

Example permissions:

- booking.create
- booking.checkin
- booking.checkout
- room.manage
- report.view
- user.manage

---

# 6. Booking System

## 6.1 Multi Room Booking

A single booking may contain multiple rooms.

Example:

- 2 Deluxe Rooms
- 1 Standard Room

This supports:

- Family bookings
- Group bookings
- Corporate bookings

---

## 6.2 Booking Structure

### Booking

Represents the master reservation transaction.

### Booking Item

Represents each room reservation inside a booking.

---

## 6.3 Booking Statuses

Recommended statuses:

- pending
- paid
- confirmed
- checked_in
- checked_out
- cancelled
- no_show
- refunded

---

## 6.4 Booking Sources

Booking sources may include:

- online
- walk_in
- phone
- front_office
- travel_agent

---

# 7. Room Management

## 7.1 Room Status

Physical rooms may have statuses:

- available
- occupied
- reserved
- dirty
- cleaning
- maintenance
- out_of_order

---

## 7.2 Room Assignment

Physical room assignment is preferably handled during check-in.

---

# 8. Room Capacity

Room types must support:

- maximum adults
- maximum children
- maximum infants
- maximum extra beds

---

# 9. Amenities

Amenities belong to room types.

Example:

- WiFi
- Breakfast
- Dinner
- TV
- Air Conditioner
- Parking

Different room types may provide different amenities.

---

# 10. Room Images

Room types support multiple images.

Example:

- thumbnail image
- gallery images
- primary image

Hotels may also have multiple images.

---

# 11. Payment System

## 11.1 Payment Methods

Supported methods:

- Midtrans
- Cash
- Bank Transfer
- EDC/Card Payment

---

## 11.2 Online Payments

Guests may pay online using Midtrans.

---

## 11.3 Onsite Payments

Front Office staff may receive direct/manual payments.

---

# 12. Reports

The system should support:

- booking reports
- occupancy reports
- revenue reports
- hotel performance reports

Reports may be filtered by:

- hotel
- date
- booking status

---

# 13. Audit Logging

Important actions should be logged.

Examples:

- booking cancellation
- room reassignment
- payment updates
- user updates

---

# 14. Development Principles

- Avoid overengineering
- Prefer modular architecture
- Use permission-based authorization
- Maintain multi-hotel scalability
- Keep business logic centralized
- Prioritize maintainability

# 15. Background Processing & Queue System

The system should support asynchronous background processing for resource-intensive operations.

Heavy or long-running tasks SHOULD use queue workers instead of synchronous HTTP execution.

Examples:

- report generation
- Excel export
- PDF generation
- email notifications
- payment follow-up actions
- analytics processing
- future WhatsApp notifications

Queue-based processing is recommended to:

- improve user experience
- reduce request timeout risks
- improve scalability
- reduce server load

Laravel queue workers should be used for asynchronous processing.
