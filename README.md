MVP specification wonders
-------------------------
Team members : ZAHRA MUSBAL 
---------------------------



Architecture:
------------

![online-shopping-architecture-slide4](https://github.com/Zahra11Mosbal11/MVP-website/assets/107762291/b76bb249-5f0c-462b-8555-4a2c3c73d8a6)




APIs and Methods :
------------------

1. User Authentication
POST /api/register
Description: Registers a new user.
Request Body: { "username": "string", "email": "string", "password": "string" }
Response: { "message": "User registered successfully", "userId": "string" }
POST /api/login
Description: Authenticates a user and returns a JWT token.
Request Body: { "email": "string", "password": "string" }
Response: { "token": "JWT string", "userId": "string" }
POST /api/logout
Description: Logs out the user (optional if using stateless JWT tokens).
Request Body: None
Response: { "message": "User logged out successfully" }
2. User Management
GET /api/users/
Description: Retrieves the details of a specific user.
Request Params: userId: "string"
Response: { "user": { "id": "string", "username": "string", "email": "string", "createdAt": "date" } }
PUT /api/users/
Description: Updates the details of a specific user.
Request Params: userId: "string"
Request Body: { "username": "string", "email": "string", "password": "string" }
Response: { "message": "User updated successfully" }
3. Product Management
GET /api/products
Description: Retrieves a list of all products.
Request Params: Optional query parameters for filtering and pagination (e.g., ?category=string&page=number&limit=number)
Response: { "products": [ { "id": "string", "name": "string", "description": "string", "price": "number", "category": "string", "stock": "number" } ] }
GET /api/products/
Description: Retrieves the details of a specific product.
Request Params: productId: "string"
Response: { "product": { "id": "string", "name": "string", "description": "string", "price": "number", "category": "string", "stock": "number" } }
POST /api/products
Description: Adds a new product to the inventory.
Request Body: { "name": "string", "description": "string", "price": "number", "category": "string", "stock": "number" }
Response: { "message": "Product added successfully", "productId": "string" }
PUT /api/products/
Description: Updates the details of a specific product.
Request Params: productId: "string"
Request Body: { "name": "string", "description": "string", "price": "number", "category": "string", "stock": "number" }
Response: { "message": "Product updated successfully" }
DELETE /api/products/
Description: Deletes a specific product from the inventory.
Request Params: productId: "string"
Response: { "message": "Product deleted successfully" }
4. Order Management
GET /api/orders
Description: Retrieves a list of all orders (admin view) or user-specific orders (user view).
Request Params: Optional query parameters for filtering and pagination (e.g., ?userId=string&page=number&limit=number)
Response: { "orders": [ { "id": "string", "userId": "string", "products": [ { "productId": "string", "quantity": "number" } ], "totalPrice": "number", "status": "string", "createdAt": "date" } ] }
GET /api/orders/
Description: Retrieves the details of a specific order.
Request Params: orderId: "string"
Response: { "order": { "id": "string", "userId": "string", "products": [ { "productId": "string", "quantity": "number" } ], "totalPrice": "number", "status": "string", "createdAt": "date" } }
POST /api/orders
Description: Creates a new order.
Request Body: { "userId": "string", "products": [ { "productId": "string", "quantity": "number" } ], "totalPrice": "number" }
Response: { "message": "Order created successfully", "orderId": "string" }
PUT /api/orders/
Description: Updates the status of a specific order.
Request Params: orderId: "string"
Request Body: { "status": "string" }
Response: { "message": "Order status updated successfully" }
DELETE /api/orders/
Description: Cancels a specific order.
Request Params: orderId: "string"
Response: { "message": "Order cancelled successfully" }
5. Category Management
GET /api/categories
Description: Retrieves a list of all product categories.
Response: { "categories": [ { "id": "string", "name": "string" } ] }
POST /api/categories
Description: Adds a new product category.
Request Body: { "name": "string" }
Response: { "message": "Category added successfully", "categoryId": "string" }
PUT /api/categories/
Description: Updates the name of a specific category.
Request Params: categoryId: "string"
Request Body: { "name": "string" }
Response: { "message": "Category updated successfully" }
DELETE /api/categories/
Description: Deletes a specific category.
Request Params: categoryId: "string"
Response: { "message": "Category deleted successfully" }

Data Model : 
------------
https://app.sqldbm.com/MySQL/Edit/p298593


User Stories: 
-------------
User Story 1: User Registration and Authentication
As a new user, I want to create an account and log in securely so that I can access my personalized shopping experience and order history.
Acceptance Criteria:
The user can register with a unique username, email, and password.
The user receives a confirmation email upon successful registration.
The user can log in using their email and password.
The user receives a JWT token upon successful login for secure session management.
The user can log out, invalidating their session.
User Story 2: Product Browsing and Search
As a shopper, I want to browse and search for products so that I can find items I am interested in purchasing.
Acceptance Criteria:
The user can view a list of products with basic information (name, price, category, brief description).
The user can filter products by category.
The user can search for products using keywords.
The user can sort products by relevance, price, and newest arrivals.
The user can view detailed information for a selected product.
User Story 3: Shopping Cart Management
As a shopper, I want to add products to my shopping cart so that I can review and manage my selections before making a purchase.
Acceptance Criteria:
The user can add products to the shopping cart from the product listing or product detail page.
The user can view the contents of their shopping cart at any time.
The user can update the quantity of each item in the shopping cart.
The user can remove items from the shopping cart.
The shopping cart persists between sessions for logged-in users.
User Story 4: Checkout Process
As a shopper, I want to complete my purchase through a streamlined checkout process so that I can receive the items I have selected.
Acceptance Criteria:
--------------------
The user can proceed to checkout from the shopping cart.
The user can enter and save shipping information.
The user can select a payment method and securely enter payment details.
The user receives an order confirmation with details of their purchase.
The order is recorded in the user's order history, and stock levels are updated accordingly.
User Story 5: Order History and Tracking
As a returning user, I want to view my past orders and track current orders so that I can keep track of my purchases and delivery status.
Acceptance Criteria:
The user can view a list of their past orders with basic information (order date, total amount, status).
The user can view detailed information for each order, including items purchased, quantities, and prices.
The user can see the current status of their order (e.g., processing, shipped, delivered).
The user can track the shipping status and view estimated delivery dates for shipped orders.
The user receives notifications via email for significant updates in their order status (e.g., order confirmed, order shipped).



Mockups : 
---------
https://balsamiq.cloud/sgpvblg/pl5n9gu


