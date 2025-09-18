# E-commerce Database Schema (MySQL)

## Overview
This project defines a **relational database schema** for a simple e-commerce store.  
It includes tables for users, products, categories, orders, payments, wishlists, and more.  

The schema is written for **MySQL 8.x** using the **InnoDB** storage engine and `utf8mb4` character set.

## Features
- **Users & Addresses**: Customers can have multiple addresses.
- **Products & Categories**: Supports many-to-many product–category assignments.
- **Suppliers**: Track product suppliers.
- **Inventory**: Quantity per product per warehouse.
- **Orders & Order Items**: Full order processing support.
- **Payments**: Linked one-to-one with orders.
- **Reviews**: Customers can leave one review per product.
- **Wishlists**: Customers can create wishlists with many products.
- **Audit Logs**: Basic system event tracking.

## Relationships
- **One-to-Many**: `users -> addresses`, `orders -> order_items`, `products -> inventory`.
- **Many-to-Many**: `products <-> categories`, `users <-> products` (via wishlists).
- **One-to-One**: `orders -> payments`.
- **Recursive**: `categories.parent_category_id` for nested categories.

## Setup Instructions
1. Clone or download this repository.
2. Open MySQL and run:
   ```sql
   SOURCE ecommerce_schema.sql;
The database ecommerce_store will be created with all tables and constraints.

Example Usage

Insert a new user:

INSERT INTO users (username, email, password_hash, first_name, last_name)
VALUES ('jdoe', 'jdoe@example.com', 'hashedpassword', 'John', 'Doe');


Add a product:

INSERT INTO products (sku, name, price, supplier_id)
VALUES ('SKU123', 'Laptop XYZ', 899.99, 1);


Create an order:

INSERT INTO orders (order_number, user_id, total_amount, status)
VALUES ('ORD1001', 1, 899.99, 'pending');

File Contents

ecommerce_schema.sql → Full MySQL schema with constraints and indexes.

README.md → Documentation for schema design and usage.

Notes

The schema uses CHECK constraints, which are fully supported in MySQL 8.0+.

ON DELETE CASCADE is used in join/mapping tables to ensure data consistency.

Customize ENUM values for order and payment status as needed.


Do you want me to also include a **diagram (ERD)** in the README, so it’s more visual
