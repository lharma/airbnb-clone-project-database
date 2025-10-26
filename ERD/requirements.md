# 🏠 ALX Airbnb Database Project

## **1. Project Overview**
This project is part of the **ALX Airbnb Database Module**, designed to help learners master real-world database design and implementation. The goal is to **design, normalize, and implement** a relational database system that models the operations of an **Airbnb-like platform**.

The system manages data about users, properties, bookings, and payments while ensuring **data integrity, scalability, and efficiency**.  
By completing this project, you will gain hands-on experience in professional database design, SQL scripting, and data modeling.

---

## **2. ERD Design Explanation**

The **Entity-Relationship Diagram (ERD)** visually represents how data is structured and how entities interact.

### **Entities and Attributes**
#### 🧑‍💻 User
- `user_id` (PK)
- `full_name`
- `email`
- `phone_number`
- `date_joined`

#### 🏠 Property
- `property_id` (PK)
- `owner_id` (FK → User.user_id)
- `title`
- `location`
- `price_per_night`
- `description`

#### 📅 Booking
- `booking_id` (PK)
- `user_id` (FK → User.user_id)
- `property_id` (FK → Property.property_id)
- `start_date`
- `end_date`
- `total_amount`
- `status`

#### 💳 Payment
- `payment_id` (PK)
- `booking_id` (FK → Booking.booking_id)
- `amount`
- `payment_method`
- `payment_date`
- `status`

#### ⭐ Review
- `review_id` (PK)
- `booking_id` (FK → Booking.booking_id)
- `rating`
- `comment`
- `review_date`

---

### **Relationships**
- A **User** can own multiple **Properties**.  
- A **User** can make multiple **Bookings**.  
- A **Booking** belongs to one **User** and one **Property**.  
- A **Booking** can have one **Payment**.  
- A **Booking** can have one **Review**.

This ERD structure ensures **clarity**, **referential integrity**, and supports future scalability (e.g., adding more features like property amenities or messages).

---

## **3. Normalization Process (Up to 3NF)**

Normalization ensures that the database design reduces redundancy and improves data consistency.

### **First Normal Form (1NF)**
- All tables have **atomic values** (no repeating groups).  
- ✅ Example: Instead of having a `phone_numbers` column with multiple values, we store only one `phone_number` per record.

### **Second Normal Form (2NF)**
- The database is in 1NF.  
- All **non-key attributes** are fully dependent on the **primary key**.  
- ✅ Example: In the `Property` table, `title` and `price_per_night` depend entirely on `property_id`, not on `owner_id`.

### **Third Normal Form (3NF)**
- The database is in 2NF.  
- No **transitive dependencies** (non-key attributes don’t depend on other non-key attributes).  
- ✅ Example: In the `Booking` table, `total_amount` depends on `booking_id`, not indirectly on `property_id` or `user_id`.

After normalization, all entities were structured to ensure:
- ✅ No duplicate data  
- ✅ Better query performance  
- ✅ Consistent and maintainable structure  

---

## **4. Database Schema Overview**

### **Users Table**
Holds user details (both guests and property owners).

| Column | Type | Constraint |
|--------|------|------------|
| user_id | SERIAL | PRIMARY KEY |
| full_name | VARCHAR(100) | NOT NULL |
| email | VARCHAR(100) | UNIQUE |
| phone_number | VARCHAR(15) |  |
| date_joined | DATE | DEFAULT CURRENT_DATE |

---

### **Properties Table**
Stores property listings.

| Column | Type | Constraint |
|--------|------|------------|
| property_id | SERIAL | PRIMARY KEY |
| owner_id | INT | FOREIGN KEY (User.user_id) |
| title | VARCHAR(150) | NOT NULL |
| location | VARCHAR(255) | NOT NULL |
| price_per_night | DECIMAL(10,2) | NOT NULL |
| description | TEXT |  |

---

### **Bookings Table**
Tracks reservations.

| Column | Type | Constraint |
|--------|------|------------|
| booking_id | SERIAL | PRIMARY KEY |
| user_id | INT | FOREIGN KEY (User.user_id) |
| property_id | INT | FOREIGN KEY (Property.property_id) |
| start_date | DATE | NOT NULL |
| end_date | DATE | NOT NULL |
| total_amount | DECIMAL(10,2) | NOT NULL |
| status | VARCHAR(50) | DEFAULT 'pending' |

---

### **Payments Table**
Stores transaction data.

| Column | Type | Constraint |
|--------|------|------------|
| payment_id | SERIAL | PRIMARY KEY |
| booking_id | INT | FOREIGN KEY (Booking.booking_id) |
| amount | DECIMAL(10,2) | NOT NULL |
| payment_method | VARCHAR(50) |  |
| payment_date | DATE | DEFAULT CURRENT_DATE |
| status | VARCHAR(50) | DEFAULT 'completed' |

---

### **Reviews Table**
Holds guest feedback.

| Column | Type | Constraint |
|--------|------|------------|
| review_id | SERIAL | PRIMARY KEY |
| booking_id | INT | FOREIGN KEY (Booking.booking_id) |
| rating | INT | CHECK (rating BETWEEN 1 AND 5) |
| comment | TEXT |  |
| review_date | DATE | DEFAULT CURRENT_DATE |

---

## **5. Sample Data Description**
The database will be seeded with **realistic sample data** using SQL `INSERT` statements.

Examples:
- Multiple **Users** (guests and hosts)
- Multiple **Properties** listed by different hosts
- **Bookings** linking users and properties
- **Payments** matching completed bookings
- **Reviews** reflecting guest experiences

This helps simulate a real-world environment for testing queries and performance.

---

## **6. Conclusion**
This project provides a **solid foundation** for building real-world database systems.  
By applying **ER modeling, normalization, schema design, and data seeding**, the database achieves:
- High performance  
- Scalability  
- Data consistency  
- Real-world readiness  

Completing this project demonstrates your ability to **design and implement** professional-grade databases aligned with industry standards.

---

🧠 *Developed as part of the ALX Airbnb Database Module.*

