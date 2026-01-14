# E-Commerce Backend API Project

## Project Overview

You will design and build the backend for **MegaMart**, a simplified e-commerce platform. This project will challenge your backend skills, requiring you to:

- Design MongoDB models for key e-commerce entities
- Build a RESTful API using Node.js, Express, and Mongoose
- Implement filtering and sorting on product listings
- Handle relationships across collections using Mongoose references
- Develop clean and modular code with proper error handling
- Place your projects on GitHub after getting them set up.  Make incremental commits as you progress
  
This project will focus purely on backend functionality. **Authentication and security are not part of this project.**

---

## Models

Note which models are referencing other documents in the database.

### Products

- CRUD operations
- Fields:
  - `name` *(string)*
  - `description` *(string)*
  - `price` *(number)*
  - `category` *(string)*
  - `stock` *(number)*
  - `images` *(array of strings for image URLs)*
- Products should support **filtering and sorting** through query parameters:
  - Filter by category, price range, and in-stock status
  - Sort by price or name (ascending or descending)

#### Example Query:

```
GET /products?category=tech&minPrice=20&maxPrice=100&inStock=true&sort=-price
```

---

### Customers

- CRUD operations
- Fields:
  - `name` *(string)*
  - `email` *(string)*
  - `address` *(string)*
  - `phone` *(string)*

---

### Shopping Carts

- One shopping cart per customer
- Fields:
  - `customer` *(reference to Customer)*
  - `items`  *(array of objects with `productId` (reference to Product) and `quantity` (number))*
- Endpoints should allow:
  - Adding a product to the cart
  - Updating quantity
  - Removing a product
  - Clearing the cart
  - Retrieving the cart (get all items in cart and include total price calculation)

---

### Orders

- Orders are placed based on the shopping cart
- Suggested fields:
  - `customer` *(reference to Customer)*
  - `items` *(copied from the cart at order time)*
  - `total` *(calculated from cart)*
  - `status` *("pending", "shipped", "delivered", "cancelled")*
  - `createdAt` *(date)*
- Endpoints should allow:
  - Placing an order from a cart
  - Viewing a customer's orders
  - Filtering orders by status
  - Updating the status of an order

---

## Project Guidelines

- Structure your project using **Models**, **Routes**, and **Controllers**
- Use Mongoose references to relate orders and shopping carts to customers and their items.
- Make use of `.populate()` to return related data where appropriate.

---

## Bonus Challenges (Optional)

- Add **pagination** to product listings using `page` and `limit` query parameters.
- Integrate **express-validator** for validating request bodies.
- Automatically reduce product stock when an order is placed.
- Allow customers to leave reviews on products.
- Integrate JWT as well as bcrypt for customers (make sure to add a password field to the Customer model as well)

---
