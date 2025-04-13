# 📦 Inventory Control Management - Database Schema

This project is designed to model an **Inventory Control Management System** using a relational database. It aims to manage users, suppliers, product items, and purchase orders efficiently.

---

## 🔧 Project Approach

The system is structured around four core entities:

1. **User Login** - for user authentication and management.
2. **Suppliers** - who provide the inventory items.
3. **Product Items** - the goods managed in inventory.
4. **Purchase Orders** - orders placed for inventory replenishment.

Each of these entities is implemented using tables within a schema named `inventory_control_management`. The schema and tables are created using PostgreSQL syntax.

---

## 📘 Schema and Table Structure

### 1. `user_login`

- **Purpose**: Manages user accounts who interact with the system.
- **Fields**:
  - `user_id`: Unique identifier for the user.
  - `user_password`: Stores user password (ideally encrypted).
  - `first_name`, `last_name`: User's personal details.
  - `sign_up_on`: Date of registration.
  - `email_id`: Contact email address.

---

### 2. `supplier`

- **Purpose**: Stores details of suppliers providing inventory items.
- **Fields**:
  - `supplier_id`: Unique identifier.
  - `supplier_name`: Company/person name.
  - `address`: Supplier’s address.
  - `registered_on`: Date of onboarding.

---

### 3. `product_items`

- **Purpose**: Contains data about individual inventory items.
- **Fields**:
  - `item_id`: Unique identifier.
  - `item_code`: Code used for internal tracking.
  - `item_name`: Descriptive name.
  - `item_type`: Type/category of the product.
  - `item_description`: Detailed description.
  - `item_image`: JSON field to store image metadata (e.g., URL, alt text).
  - `brand_name`: Associated brand.
  - `supplier_id`: Foreign key linked to `supplier`.
  - `cost_per_unit`: Price per unit.
  - `stock_count`: Number of units available in stock.

---

### 4. `purchase_orders`

- **Purpose**: Tracks all the inventory purchase transactions.
- **Fields**:
  - `order_id`: Unique identifier.
  - `item_id`: Foreign key referencing `product_items`.
  - `supplier_id`: Foreign key referencing `supplier`.
  - `order_date`: When the order was placed.
  - `quantity`: Number of items ordered.
  - `delivery_date`: When the order was delivered.
  - `is_delivered`: Boolean indicating delivery status.
  - `payment_id`: ID for tracking the payment.
  - `is_paid`: Boolean indicating if payment is completed.

---

## 🧠 Key Terminologies

| Term             | Description |
|------------------|-------------|
| **Schema**       | Logical container for database objects. Helps organize and group tables. |
| **Primary Key**  | Unique identifier for records in a table. |
| **Foreign Key**  | Links records in one table to those in another. Maintains referential integrity. |
| **JSON**         | Used here for storing image metadata flexibly (e.g., `{"url": "...", "alt": "..."}`) |
| **CASCADE**      | Option in `DROP SCHEMA` to automatically delete all dependent objects. |
| **Boolean**      | Data type representing True/False values (used for delivery and payment statuses). |

---

## ✅ Benefits of This Design

- Ensures **data integrity** through proper use of primary and foreign keys.
- Supports **scalability** with modular table design.
- **JSON image support** allows for extensible item metadata.
- Enables detailed **reporting and tracking** for orders and inventory.

---

## 🚀 Possible Extensions

- Add user roles (admin, manager, viewer).
- Integrate payment tracking and invoices.
- Include automated low-stock alerts.
- API endpoints for CRUD operations on each table.

