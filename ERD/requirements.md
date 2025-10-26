# 🧩 Entity–Relationship (ER) Diagram Requirements

## 📘 Overview
This document defines the entities, attributes, and relationships for the **ALX Airbnb Database Project**.  
It serves as a blueprint for the database design, showing how key entities interact to model a simplified Airbnb-like system.

---

## 🧠 Key Entities and Their Attributes

### 🧍 User
| Field | Type | Description |
|--------|------|-------------|
| user_id | INT (PK) | Unique ID for each user |
| first_name | VARCHAR | User’s first name |
| last_name | VARCHAR | User’s last name |
| email | VARCHAR | User’s email address |
| phone | VARCHAR | Contact number |
| user_type | ENUM('guest','host') | Defines user role |
| created_at | TIMESTAMP | When the user joined |

---

### 🏠 Property
| Field | Type | Description |
|--------|------|-------------|
| property_id | INT (PK) | Unique property ID |
| host_id | INT (FK → User.user_id) | Host who owns the property |
| title | VARCHAR | Property title |
| description | TEXT | Short property description |
| location | VARCHAR | City or address |
| price_per_night | DECIMAL | Cost per night |
| created_at | TIMESTAMP | Date property was listed |

---

### 📅 Booking
| Field | Type | Description |
|--------|------|-------------|
| booking_id | INT (PK) | Unique booking ID |
| user_id | INT (FK → User.user_id) | Guest who made the booking |
| property_id | INT (FK → Property.property_id) | Property booked |
| check_in | DATE | Start date |
| check_out | DATE | End date |
| total_amount | DECIMAL | Total cost of booking |
| booking_status | ENUM('pending','confirmed','cancelled') | Current booking state |
| created_at | TIMESTAMP | Date booking was created |

---

### 💳 Payment
| Field | Type | Description |
|--------|------|-------------|
| payment_id | INT (PK) | Unique payment ID |
| booking_id | INT (FK → Booking.booking_id) | Linked booking |
| amount | DECIMAL | Amount paid |
| payment_date | TIMESTAMP | Date of payment |
| payment_method | ENUM('credit_card','paypal','mobile_money') | Mode of payment |
| payment_status | ENUM('successful','failed','pending') | Payment outcome |

---

## 🔗 Relationships
| Relationship | Description |
|---------------|-------------|
| User (1) → Property (N) | One host can own many properties |
| User (1) → Booking (N) | One guest can make many bookings |
| Property (1) → Booking (N) | One property can have many bookings |
| Booking (1) → Payment (1) | Each booking has one payment record |

---

## 🖼️ ER Diagram
Insert your Draw.io (or similar) diagram link or upload the image here:  
**`ERD Diagram File:`** `airbnb_erd.png`

---

## ✅ Notes
- All entities include `created_at` timestamps for tracking.  
- Foreign keys enforce referential integrity.  
- ENUM types restrict invalid values.  
