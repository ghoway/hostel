# Entity Relationship Overview (ERD)

---

# Core Entities

## hotels

Represents hotel branches.

Relationships:

- has many room_types
- has many rooms
- has many bookings
- has many users

---

## room_types

Represents sellable room categories.

Examples:

- Standard
- Deluxe
- Superior

Relationships:

- belongs to hotel
- has many rooms
- has many amenities
- has many images

---

## rooms

Represents physical hotel rooms.

Examples:

- Room 101
- Room 202

Relationships:

- belongs to hotel
- belongs to room_type

---

## amenities

Represents room amenities.

Examples:

- WiFi
- Breakfast
- Dinner

Relationships:

- belongs to many room_types

---

## room_type_images

Represents room type gallery images.

Relationships:

- belongs to room_type

---

## hotel_images

Represents hotel gallery images.

Relationships:

- belongs to hotel

---

## bookings

Represents master reservation transactions.

Relationships:

- belongs to hotel
- belongs to guest/user
- has many booking_items
- has many payments

---

## booking_items

Represents room reservations inside a booking.

Relationships:

- belongs to booking
- belongs to room_type
- optionally belongs to assigned room

---

## payments

Represents payment transactions.

Relationships:

- belongs to booking

---

## users

Represents:

- guests
- front office staff
- administrators

Relationships:

- optionally belongs to hotel
- has roles
- has permissions

---

# Relationship Notes

- One booking may contain multiple booking items
- Guests reserve room types, not physical rooms
- Physical rooms are assigned later operationally
- Amenities belong to room types
- Pricing belongs to room types
