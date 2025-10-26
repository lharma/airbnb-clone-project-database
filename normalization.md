
# Database Normalization (Airbnb Database Project)

Database normalization is the process of organizing data in a way that reduces redundancy and improves data integrity.  
In this Airbnb database project, normalization ensures that user, property, and booking data are stored efficiently and can be easily maintained or updated.

---

## Why Normalization Is Important
- Prevents duplicate data (e.g., same user details stored multiple times)
- Makes updates and deletions easier
- Keeps the database consistent and accurate
- Improves query performance and storage efficiency

---

## Step-by-Step Normalization

### 1. First Normal Form (1NF)
**Rule:** Each column must contain only one value (no repeating groups or lists).

**Example (Before 1NF)**

| user_id | name  | emails                |
|----------|-------|-----------------------|
| 1        | Alice | alice@gmail.com, alice@yahoo.com |

Here, the `emails` column has multiple values.

**After Applying 1NF**

| user_id | name  | email             |
|----------|-------|------------------|
| 1        | Alice | alice@gmail.com  |
| 1        | Alice | alice@yahoo.com  |

Now each cell contains a single value. The table is in **1NF**.

---

### 2. Second Normal Form (2NF)
**Rule:** Be in 1NF and ensure every non-key attribute depends on the entire primary key.

**Example (Before 2NF)**

| property_id | host_id | host_name | property_name | location |
|--------------|----------|------------|----------------|-----------|
| 101 | 12 | John Doe | Beach Apartment | Accra |

Here, `host_name` depends only on `host_id`, not on the full primary key (`property_id`, `host_id`).

**After Applying 2NF**
We separate the data into two tables:

**Hosts Table**
| host_id | host_name |
|----------|------------|
| 12       | John Doe   |

**Properties Table**
| property_id | property_name | location | host_id |
|--------------|----------------|-----------|----------|
| 101          | Beach Apartment | Accra     | 12       |

Now, every non-key column depends on the full key. The data is in **2NF**.

---

### 3. Third Normal Form (3NF)
**Rule:** Be in 2NF and remove transitive dependencies (non-key columns should not depend on other non-key columns).

**Example (Before 3NF)**

| booking_id | user_id | property_id | city     | postal_code |
|-------------|----------|--------------|-----------|--------------|
| 2001 | 1 | 101 | Accra | 00233 |

Here, `postal_code` depends on `city`, not on `booking_id`.

**After Applying 3NF**

**Bookings Table**
| booking_id | user_id | property_id |
|-------------|----------|--------------|
| 2001 | 1 | 101 |

**Cities Table**
| city_id | city_name | postal_code |
|----------|------------|--------------|
| 1 | Accra | 00233 |

**Properties Table**
| property_id | property_name | city_id |
|--------------|----------------|----------|
| 101 | Beach Apartment | 1 |

Now, each non-key column depends only on its key — the database is in **3NF**.

---

## Final Normalized Structure (3NF)
After applying all normalization steps, the Airbnb-like database design includes these main tables:

| Table | Key Attribute | Purpose |
|--------|----------------|----------|
| **Users** | `user_id` | Stores user account info |
| **Hosts** | `host_id` | Stores host information |
| **Properties** | `property_id` | Stores property listings |
| **Bookings** | `booking_id` | Links users to properties they book |
| **Payments** | `payment_id` | Tracks transactions for each booking |
| **Cities** | `city_id` | Stores city and postal code details |

---

## Summary
Normalization ensures that:
- Data redundancy is minimized  
- Each entity has a clear purpose  
- Relationships between tables are well-defined  
- The database is easy to scale and maintain  

A well-normalized database allows Airbnb-like systems to efficiently handle thousands of users, properties, and bookings without confusion or data loss.
