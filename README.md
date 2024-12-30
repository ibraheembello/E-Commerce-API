# E-Commerce API

Project from [Backend Development Roadmap](https://roadmap.sh/projects/ecommerce-api)

## Overview

A RESTful API for an e-commerce platform with features including user authentication, product management, shopping cart functionality, and payment processing using Stripe.

## Features

- User authentication with JWT
- Product management (CRUD operations)
- Shopping cart functionality
- Order processing
- Admin panel functionality
- Stripe payment integration
- Inventory management

## Prerequisites

- Node.js (v16.20.1 or higher)
- MongoDB
- Stripe account for payment processing

## Installation

1. Clone the repository
2. Install dependencies:

```bash
npm install
```

3. Create a `.env` file with the following variables:

```
JWT_SECRET=your_jwt_secret
STRIPE_SECRET_KEY=your_stripe_secret_key
MONGODB_URI=your_mongodb_connection_string
```

## API Endpoints

### Authentication

- `POST /api/auth/register` - Register a new user
- `POST /api/auth/login` - Login user

### Products

- `GET /api/products` - Get all products
- `GET /api/products/:id` - Get single product
- `POST /api/products` - Create product (Admin only)
- `PUT /api/products/:id` - Update product (Admin only)
- `DELETE /api/products/:id` - Delete product (Admin only)

### Cart

- `GET /api/cart` - Get user's cart
- `POST /api/cart/items` - Add item to cart
- `PUT /api/cart/items/:productId` - Update cart item quantity
- `DELETE /api/cart/items/:productId` - Remove item from cart

### Orders

- `POST /api/checkout` - Create order and process payment
- `GET /api/orders` - Get user's orders
- `GET /api/orders/:id` - Get specific order

### Admin Routes

- `GET /api/admin/orders` - Get all orders
- `PUT /api/admin/orders/:id` - Update order status
- `GET /api/admin/users` - Get all users

## Example API Usage

### Register User

```bash
curl -X POST http://localhost:3000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"email": "user@example.com", "password": "password123"}'
```

### Login

```bash
curl -X POST http://localhost:3000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email": "user@example.com", "password": "password123"}'
```

### Create Product (Admin)

```bash
curl -X POST http://localhost:3000/api/products \
  -H "Authorization: Bearer YOUR_JWT_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"name": "Product Name", "description": "Description", "price": 99.99, "inventory": 100}'
```

## Running the Server

```bash
node index.js
```

Server will start on port 3000 by default or PORT environment variable if specified.

## Testing

Use Postman or curl to test the API endpoints. Remember to include the JWT token in the Authorization header for protected routes:

```
Authorization: Bearer YOUR_JWT_TOKEN
```

## Security Features

- Password hashing using bcryptjs
- JWT authentication
- Admin role validation
- Protected routes
- Inventory validation

## Project Structure

```
├── index.js          # Main application file
├── package.json      # Project dependencies
├── .env             # Environment variables
└── .gitignore       # Git ignore file
```

## Technical Decisions

- **Express.js**: Lightweight and flexible Node.js web framework
- **MongoDB**: NoSQL database for flexible data storage
- **Mongoose**: MongoDB object modeling for Node.js
- **JWT**: Stateless authentication mechanism
- **Stripe**: Secure payment processing
- **bcryptjs**: Password hashing

## License

MIT

## Project Source

This project is part of the Backend Development Roadmap:
[E-Commerce API Project](https://roadmap.sh/projects/ecommerce-api)
