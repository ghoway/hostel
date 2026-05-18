# Detailed Entity Relationship Design

---

# hotels

Represents hotel branches.

## Columns

- id
- name
- slug
- address
- city
- province
- postal_code
- phone
- email
- description
- checkin_time
- checkout_time
- is_active
- created_at
- updated_at
- deleted_at

---

# hotel_images

Represents hotel gallery images.

## Columns

- id
- hotel_id
- image_path
- is_primary
- sort_order
- created_at
- updated_at

---

# room_types

Represents sellable room categories.

Examples:

- Standard
- Deluxe
- Superior

## Columns

- id
- hotel_id
- name
- slug
- description
- base_price
- max_adult
- max_child
- max_infant
- max_extra_bed
- total_rooms
- is_active
- created_at
- updated_at
- deleted_at

---

# room_type_images

Represents room type image galleries.

## Columns

- id
- room_type_id
- image_path
- is_primary
- sort_order
- created_at
- updated_at

---

# amenities

Represents available amenities.

## Columns

- id
- name
- slug
- icon
- created_at
- updated_at

---

# amenity_room_type

Pivot table for room type amenities.

## Columns

- room_type_id
- amenity_id

---

# rooms

Represents physical hotel rooms.

Examples:

- 101
- 202
- 305

## Columns

- id
- hotel_id
- room_type_id
- room_number
- floor
- status
- notes
- created_at
- updated_at
- deleted_at

---

# users

Represents guests and staff.

## Columns

- id
- hotel_id (nullable for super admin)
- name
- email
- phone
- password
- email_verified_at
- is_active
- created_at
- updated_at
- deleted_at

---

# bookings

Represents master reservation transactions.

## Columns

- id
- hotel_id
- user_id (nullable for guest walk-in)
- booking_number
- booking_source
- status
- guest_name
- guest_email
- guest_phone
- checkin_date
- checkout_date
- subtotal
- tax_amount
- service_amount
- discount_amount
- grand_total
- notes
- expires_at
- created_by
- created_at
- updated_at
- deleted_at

---

# booking_items

Represents room reservations inside bookings.

## Columns

- id
- booking_id
- room_type_id
- room_id (nullable until assigned)
- room_type_name_snapshot
- room_price_snapshot
- adult_count
- child_count
- infant_count
- extra_bed_count
- subtotal
- created_at
- updated_at

---

# payments

Represents booking payment transactions.

## Columns

- id
- booking_id
- payment_method
- payment_gateway
- transaction_reference
- amount
- status
- paid_at
- metadata
- created_at
- updated_at
- deleted_at

---

# audit_logs

Represents audit activities.

## Columns

- id
- user_id
- action
- entity_type
- entity_id
- old_values
- new_values
- ip_address
- user_agent
- created_at

---

# Recommended Indexes

## bookings

Indexes:

- hotel_id
- booking_number
- status
- checkin_date
- checkout_date
- expires_at

---

## booking_items

Indexes:

- booking_id
- room_type_id
- room_id

---

## rooms

Indexes:

- hotel_id
- room_type_id
- status
- room_number

---

## payments

Indexes:

- booking_id
- status
- transaction_reference

---

# Relationship Summary

## hotels

- has many room_types
- has many rooms
- has many bookings
- has many users

---

## room_types

- belongs to hotel
- has many rooms
- belongs to many amenities
- has many images

---

## rooms

- belongs to hotel
- belongs to room_type

---

## bookings

- belongs to hotel
- belongs to user
- has many booking_items
- has many payments

---

## booking_items

- belongs to booking
- belongs to room_type
- optionally belongs to room

---

## payments

- belongs to booking
