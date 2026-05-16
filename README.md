# MegaMind Backend

Authentication backend for the MegaMind platform built with Express.js and MongoDB.

## Features

- ✅ User registration with validation
- ✅ Secure login with JWT tokens
- ✅ Password hashing with bcryptjs
- ✅ Protected routes with authentication middleware
- ✅ MongoDB integration with Mongoose
- ✅ Input validation with express-validator
- ✅ CORS enabled for frontend integration

## Installation

```bash
npm install
```

## Setup

1. Create `.env` file in the root directory:
```
PORT=5000
MONGODB_URI=mongodb://localhost:27017/megamind
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production
```

2. Make sure MongoDB is running:
```bash
mongod
```

3. Start the server:
```bash
npm run dev
```

## API Endpoints

### Register
**POST** `/api/auth/register`

Body:
```json
{
  "username": "johndoe",
  "password": "password123"
}
```

Response:
```json
{
  "message": "User registered successfully",
  "token": "eyJhbGciOiJIUzI1NiIs...",
  "user": {
    "id": "user_id",
    "username": "johndoe"
  }
}
```

### Login
**POST** `/api/auth/login`

Body:
```json
{
  "username": "johndoe",
  "password": "password123"
}
```

Response:
```json
{
  "message": "Login successful",
  "token": "eyJhbGciOiJIUzI1NiIs...",
  "user": {
    "id": "user_id",
    "username": "johndoe"
  }
}
```

### Get Profile (Protected)
**GET** `/api/auth/profile`

Headers:
```
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
```

Response:
```json
{
  "user": {
    "id": "user_id",
    "username": "johndoe",
    "createdAt": "2023-09-10T12:34:56.789Z"
  }
}
```

## Project Structure

```
├── controllers/
│   └── authController.js    # Auth logic
├── middleware/
│   └── auth.js              # JWT verification
├── models/
│   └── User.js              # User schema
├── routes/
│   └── auth.js              # Auth routes
├── server.js                # Express app
├── .env.example             # Environment template
└── package.json
```
