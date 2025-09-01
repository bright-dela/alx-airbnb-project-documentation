# ALX Airbnb Project - Backend Requirements

## 1. User Authentication

**Description:**  
Handles user registration, login, password management, and profile authentication.

**API Endpoints:**

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/auth/register/` | POST | Register a new user |
| `/api/auth/login/` | POST | Authenticate a user and return a token |
| `/api/auth/logout/` | POST | Logout user and invalidate session |
| `/api/auth/password-reset/` | POST | Request password reset link |
| `/api/auth/password-reset-confirm/` | POST | Reset password using token |

**Input / Output Specifications:**

- **Register**
  - Input: `{ "username": "string", "email": "string", "password": "string" }`
  - Output: `{ "id": "uuid", "username": "string", "email": "string", "token": "jwt" }`
- **Login**
  - Input: `{ "email": "string", "password": "string" }`
  - Output: `{ "token": "jwt", "user": { "id": "uuid", "username": "string", "email": "string" } }`

**Validation Rules:**
- Email must be unique and valid format
- Password minimum 8 characters, at least 1 number and 1 special character
- Username must be alphanumeric, 3-30 characters

**Performance Criteria:**
- Registration and login response time < 500ms under normal load
- JWT token expires after 24 hours

---

## 2. Property Management

**Description:**  
Allows hosts to create, update, and manage property listings. Guests can view and search properties.

**API Endpoints:**

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/properties/` | GET | List all properties |
| `/api/properties/` | POST | Create a new property listing |
| `/api/properties/{id}/` | GET | Retrieve a specific property |
| `/api/properties/{id}/` | PUT | Update property details |
| `/api/properties/{id}/` | DELETE | Remove a property |

**Input / Output Specifications:**

- **Create Property**
  - Input:  
  ```json
  {
    "title": "string",
    "description": "string",
    "location": "string",
    "price_per_night": "decimal",
    "max_guests": "integer",
    "amenities": ["string"]
  }


{
  "id": "uuid",
  "title": "string",
  "description": "string",
  "location": "string",
  "price_per_night": "decimal",
  "max_guests": "integer",
  "amenities": ["string"],
  "host_id": "uuid"
}


{
  "user_id": "uuid",
  "property_id": "uuid",
  "check_in": "YYYY-MM-DD",
  "check_out": "YYYY-MM-DD",
  "guests": "integer",
  "payment_method": "string"
}
Output:

json
Copy code
{
  "booking_id": "uuid",
  "status": "confirmed",
  "total_price": "decimal",
  "payment_status": "paid",
  "check_in": "YYYY-MM-DD",
  "check_out": "YYYY-MM-DD"
}
Validation Rules:

Check-in date must be before check-out date

Property availability must be verified before booking

Guests ≤ max_guests for property

Payment must be successfully processed before confirming

Performance Criteria:

Booking confirmation < 1 second under normal load

Support concurrent booking requests without double-booking

Notes:

All endpoints must return proper HTTP status codes (200 OK, 201 Created, 400 Bad Request, 401 Unauthorized, 404 Not Found)

All responses should be JSON-formatted

Rate limiting: 100 requests/min per user

All sensitive data must be encrypted at rest and in transit

yaml
Copy code

