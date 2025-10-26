# Database Seeding (DML)

## Overview
This folder contains the SQL Data Manipulation Language (DML) scripts used to populate the **Airbnb Database Project** with sample data.  
The data simulates real-world usage — including users, hosts, properties, bookings, and payments — to make the database ready for testing and queries.

The goal of this stage is to provide realistic sample data that helps demonstrate relationships and interactions between different entities.

---

## Files in This Directory

| File | Description |
|------|--------------|
| **seed.sql** | SQL script that inserts sample data into all tables. |
| **README.md** | Explanation of the seeding process and data organization. |

---

## Seeding Objectives
The `seed.sql` script will:
1. Insert test data into **Users**, **Hosts**, **Cities**, **Properties**, **Bookings**, and **Payments** tables.
2. Ensure data consistency (e.g., each booking references valid users and properties).
3. Simulate real scenarios like:
   - Users booking properties in different cities.
   - Hosts owning multiple properties.
   - Payments linked to completed bookings.

---

## Example of Sample Data

### 1. Users
```sql
INSERT INTO users (full_name, email, phone_number, created_at)
VALUES
('Alice Johnson', 'alice@example.com', '0541234567', NOW()),
('Michael Smith', 'michael@example.com', '0209876543', NOW()),
('Sarah Brown', 'sarah@example.com', '0248765432', NOW());

