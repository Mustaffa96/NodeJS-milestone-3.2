# Node.js JWT Authentication API

A lightweight and secure authentication API built with Node.js, Express, and JWT.

## Features

- User registration and login
- JWT-based authentication
- Protected routes
- Password hashing with bcrypt
- MongoDB integration
- Swagger API documentation

## Quick Start

1. Install dependencies:
```bash
npm install
```

2. Configure environment variables:
- Copy `.env.example` to `.env`
- Update the values in `.env`:
  - `MONGODB_URI`: Your MongoDB connection string
  - `JWT_SECRET`: Your secret key for JWT
  - `PORT`: Server port (default: 3000)

3. Start the server:
```bash
npm run dev
```

4. Access Swagger Documentation:
- Open `http://localhost:3000/api-docs` in your browser
- Interactive API documentation with testing capability

## Authentication Flow

To access protected routes, follow these steps:

1. Register a new user:
```bash
POST /api/auth/register
{
  "username": "testuser",
  "email": "test@example.com",
  "password": "password123"
}
```

2. Login to get JWT token:
```bash
POST /api/auth/login
{
  "email": "test@example.com",
  "password": "password123"
}
```

3. Use the received token for protected routes:
```bash
GET /api/auth/profile
Authorization: Bearer <token-from-login-response>
```

**Important**: Always use the token received from the login response. Sample or self-generated tokens will not work as they need to be properly signed with the server's secret key.

## API Endpoints

### Public Routes
- `POST /api/auth/register` - Register a new user
  ```json
  {
    "username": "user123",
    "email": "user@example.com",
    "password": "password123"
  }
  ```

- `POST /api/auth/login` - Login user
  ```json
  {
    "email": "user@example.com",
    "password": "password123"
  }
  ```

### Protected Routes
- `GET /api/auth/profile` - Get user profile
  - Requires valid JWT token in Authorization header
  - Format: `Authorization: Bearer <token>`
  - Token must be obtained from login response

## Technologies Used

- Node.js & Express
- MongoDB & Mongoose
- JWT (jsonwebtoken)
- bcryptjs for password hashing
- dotenv for environment variables
- Swagger UI for API documentation
