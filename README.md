# Final Project: E-Commerce Backend API Project

## Project Overview

You will design and build the backend for **MegaMart**, a simplified e-commerce platform. This project will challenge your backend skills, requiring you to:

- Build a RESTful API using Node.js, Express, and MongoDB
- Implement filtering and sorting on product listings
- Handle relationships across collections using Mongoose references (Make use of `.populate()` to return related data)
- Develop clean and modular code with proper error handling
- Place your projects on GitHub after getting them set up.  Make incremental commits as you progress
  
This project will focus purely on backend functionality. **Authentication and route protection with JWT are not required for this project.**

---

## Models

Note which models are referencing other documents in the database.

It's up to you to figure out what properties should be required and/or unique

### Products

- CRUD operations (GET, GET by ID, POST, PUT, DELETE)
- Fields:
  - `name` *(string)*
  - `description` *(string)*
  - `price` *(number)*
  - `category` *(string)*
  - `stock` *(number)*
  - `images` *(array of strings for image URLs)* (optional)
- Products should support **filtering and sorting** through query parameters:
  - Filter by category, price range, and in-stock status
  - Sort by price or name (ascending or descending)

#### Example Query:

```
GET /products?category=tech&minPrice=20&maxPrice=100&inStock=true&sortBy=price&sortOrder=desc
```

---

### Customers

- CRUD operations (GET, GET by ID, POST, PUT, DELETE)
- Fields:
  - `name` *(string)*
  - `email` *(string)*
  - `address` *(string)*
  - `phone` *(string)*

---

### Shopping Carts

- Fields:
  - `customer` *(reference to Customer)*
  - `products`  *(array of objects with `productId` (reference to Product) (required) and `quantity` (number) (stretch goal))*
- Endpoints should allow:
  - Creating the cart (One shopping cart per customer)
  - Adding a product to the cart 
  - Removing a product
  - Clearing the cart
  - Retrieving the cart (get all items in cart and include total price calculation)
  - Update quantity (stretch goal)

---

### Orders

- Orders are placed based on the shopping cart
- Suggested fields:
  - `customer` *(reference to Customer)*
  - `products` *(copied from the cart at order time)*
  - `totalPrice` *(calculated from cart)*
  - `status` *("pending", "shipped", "delivered", "cancelled")*
- Endpoints should allow:
  - Placing an order from a cart
  - Viewing a customer's orders
  - Filtering orders by status
  - Updating the status of an order

When an order is placed, the cart that was used should be cleared of all items.

---

## Bonus Challenges (Optional)

- Add **pagination** to product listings using `page` and `limit` query parameters.
- Automatically reduce product stock when an order is placed.
- Allow customers to leave reviews on products by adding a Review model
- Integrate JWT as well as bcrypt for customers (make sure to add a password field to the Customer model as well).  Make it so a customer can only view their orders if they have a JWT token
- Deploy your project to Render

---
