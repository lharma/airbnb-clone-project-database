
# Database Schema Design (DDL)

## Overview
This folder contains the SQL Data Definition Language (DDL) scripts that define the structure of the **Airbnb Database Project**.  
The schema includes tables, primary keys, foreign keys, and constraints that ensure data integrity and efficient relationships among all entities.

The goal of this task is to create a **normalized and well-structured database** capable of managing users, hosts, properties, bookings, and payments in an Airbnb-like system.

---

## Files in This Directory

| File | Description |
|------|--------------|
| **schema.sql** | SQL script containing all `CREATE TABLE` statements and constraints. |
| **README.md** | Explains the purpose of the schema and how to execute it. |
| **normalization.md** | Describes the normalization process applied up to the third normal form (3NF). |

---

## Entities in the Schema

### 1. Users
Stores information about users who can make bookings.

| Column | Type | Description |
|---------|------|-------------|
| user_id | SERIAL (PK) | Unique ID for each user |
| full_name | VARCHAR(100) | User’s full name |
| email | VARCHAR(100) | User’s email address |
| phone_number | VARCHAR(20) | User’s contact number |
| created_at | TIMESTAMP | Account creation date |

---

### 2. Hosts
Stores information about property owners or managers.

| Column | Type | Description |
|---------|------|-------------|
| host_id | SERIAL (PK) | Unique ID for each host |
| full_name | VARCHAR(100) | Host’s full name |
| email | VARCHAR(100) | Host’s contact email |
| phone_number | VARCHAR(20) | Host’s contact number |

---

### 3. Properties
Contains details about each property listed by a host.

| Column | Type | Description |
|---------|------|-------------|
| property_id | SERIAL (PK) | Unique ID for each property |
| host_id | INT (FK) | References the host who owns the property |
| property_name | VARCHAR(150) | Name of the property |
| description | TEXT | Property description |
| city_id | INT (FK) | References the city where the property is located |
| price_per_night | DECIMAL(10,2) | Cost per night |
| created_at | TIMESTAMP | Date when property was added |

---

### 4. Cities
Stores city and postal code details.

| Column | Type | Description |
|---------|------|-------------|
| city_id | SERIAL (PK) | Unique ID for each city |
| city_name | VARCHAR(100) | City name |
| postal_code | VARCHAR(20) | Postal code |

---

### 5. Bookings
Tracks reservations made by users for properties.

| Column | Type | Description |
|---------|------|-------------|
| booking_id | SERIAL (PK) | Unique ID for each booking |
| user_id | INT (FK) | References the user who made the booking |
| property_id | INT (FK) | References the booked property |
| check_in_date | DATE | Start date of booking |
| check_out_date | DATE | End date of booking |
| status | VARCHAR(50) | Booking status (e.g., confirmed, canceled) |
| created_at | TIMESTAMP | Date the booking was made |

---

### 6. Payments
Stores information about transactions related to bookings.

| Column | Type | Description |
|---------|------|-------------|
| payment_id | SERIAL (PK)_
