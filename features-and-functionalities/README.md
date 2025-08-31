# Airbnb Clone - Backend Features and Functionalities

This document outlines the **core features and technical requirements** of the Airbnb Clone backend.  
It is supported by a visual diagram (`features.png`) created in **Draw.io**, stored in this directory.

---

## 🔑 Core Functionalities

### 1. User Management
- **Registration**: Users can sign up as guests or hosts.
- **Authentication**: Secure login via email & password (JWT). Optional OAuth (Google, Facebook).
- **Profile Management**: Update profile photo, contact info, preferences.

### 2. Property Listings Management
- **Add Listings**: Hosts create listings with details (title, description, price, amenities, availability).
- **Edit/Delete Listings**: Hosts manage their listings.

### 3. Search and Filtering
- Search by **location**, **price range**, **number of guests**, **amenities**.
- Pagination for large result sets.

### 4. Booking Management
- **Booking Creation**: Guests book properties for specific dates, avoiding double bookings.
- **Booking Cancellation**: Guests/hosts cancel under policies.
- **Booking Status Tracking**: Pending, confirmed, canceled, completed.

### 5. Payment Integration
- Secure gateways (Stripe, PayPal).
- Upfront guest payments.
- Automated host payouts after stays.
- Multi-currency support.

### 6. Reviews and Ratings
- Guests leave reviews & ratings for properties.
- Hosts can respond.
- Reviews are tied to completed bookings.

### 7. Notifications System
- **Email & in-app notifications** for:
  - Booking confirmations
  - Cancellations
  - Payment updates

### 8. Admin Dashboard
- Manage & monitor:
  - Users
  - Listings
  - Bookings
  - Payments

---

## 🛠️ Technical Requirements

### 1. Database
- Relational DB (PostgreSQL/MySQL).
- Tables:
  - Users
  - Properties
  - Bookings
  - Reviews
  - Payments

### 2. API Development
- RESTful APIs (GET, POST, PUT/PATCH, DELETE).
- Proper status codes & error handling.
- Optional GraphQL for complex queries.

### 3. Authentication & Authorization
- JWT for secure sessions.
- RBAC (Guests, Hosts, Admins).

### 4. File Storage
- Store property images & profile photos (AWS S3, Cloudinary, or file storage fallback).

### 5. Third-Party Services
- Email services: SendGrid / Mailgun.

### 6. Error Handling & Logging
- Centralized error handling.
- Request/response logging.

---

## 🚀 Non-Functional Requirements

- **Scalability**: Modular architecture, horizontal scaling.
- **Security**: Encrypted sensitive data, firewalls, rate-limiting.
- **Performance**: Caching (Redis), optimized DB queries.
- **Testing**: Unit & integration tests (pytest), automated API tests.

---

## 📊 Visual Diagram

The following diagram (`features.png`) summarizes the system:

- Users (Guests, Hosts, Admins)  
- Property Listings  
- Booking System  
- Payments  
- Reviews  
- Notifications  
- Admin Dashboard  

> Open `features.png` to view the full diagram created in Draw.io.
