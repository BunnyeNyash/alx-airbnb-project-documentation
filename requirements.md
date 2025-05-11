# Requirement Specifications for Airbnb Clone Backend Features

## Objective
This document outlines the technical and functional requirement specifications for three key backend features of the ALX Airbnb Clone project: User Authentication, Property Management, and Booking System. These specifications include API endpoints, input/output details, validation rules, and performance criteria, ensuring a scalable, secure, and robust rental marketplace backend. The features are derived from Task 0's core functionalities (`features-and-functionalities/`), Task 1's use cases (`use-case-diagram/`), Task 2's user stories (`user-stories/`), Task 3's data flow diagram (`data-flow-diagram/`), and Task 4's property booking flowchart (`flowcharts/`).

## 1. User Authentication
### Overview
User Authentication enables Guests, Hosts, and Admins to register, log in, and access the Airbnb Clone platform securely. It supports email/password authentication and JWT-based session management, with role-based access control (RBAC) to differentiate permissions.

### API Endpoints
1. **Register User**
   - **Method**: POST
   - **URL**: `/api/v1/auth/register`
   - **Description**: Creates a new user account (Guest or Host).
2. **Login User**
   - **Method**: POST
   - **URL**: `/api/v1/auth/login`
   - **Description**: Authenticates a user and returns a JWT token.

### Input Specifications
- **Register User**:
  - **Request Body** (JSON):
    ```json
    {
      "email": "string",
      "password": "string",
      "first_name": "string",
      "last_name": "string",
      "role": "string" // "guest" or "host"
    }
    ```
  - **Fields**:
    - `email`: User's email address (e.g., "user@example.com").
    - `password`: Password (min 8 characters).
    - `first_name`: User's first name (max 50 characters).
    - `last_name`: User's last name (max 50 characters).
    - `role`: User role ("guest" or "host").
- **Login User**:
  - **Request Body** (JSON):
    ```json
    {
      "email": "string",
      "password": "string"
    }
    ```
  - **Fields**:
    - `email`: User's email address.
    - `password`: User's password.

### Output Specifications
- **Register User**:
  - **Success Response** (201 Created):
    ```json
    {
      "status": "success",
      "message": "User registered successfully",
      "data": {
        "user_id": "string",
        "email": "string",
        "role": "string"
      }
    }
    ```
  - **Error Response** (400 Bad Request):
    ```json
    {
      "status": "error",
      "message": "Email already exists"
    }
    ```
- **Login User**:
  - **Success Response** (200 OK):
    ```json
    {
      "status": "success",
      "message": "Login successful",
      "data": {
        "user_id": "string",
        "email": "string",
        "role": "string",
        "token": "string" // JWT token
      }
    }
    ```
  - **Error Response** (401 Unauthorized):
    ```json
    {
      "status": "error",
      "message": "Invalid credentials"
    }
    ```

### Validation Rules
- **Register User**:
  - `email`: Required, valid email format (regex: `^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$`), unique in Users table.
  - `password`: Required, min 8 characters, must include at least one uppercase letter, one lowercase letter, one number, and one special character (regex: `^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$`).
  - `first_name`, `last_name`: Required, max 50 characters, letters and spaces only.
  - `role`: Required, must be "guest" or "host".
- **Login User**:
  - `email`: Required, valid email format.
  - `password`: Required, non-empty.
- Passwords are hashed (e.g., bcrypt) before storage.

### Performance Criteria
- **Response Time**: < 200 ms for login, < 300 ms for registration (under normal load).
- **Scalability**: Handle 10,000 concurrent users with horizontal scaling (load balancers).
- **Security**: Use HTTPS, JWT with 24-hour expiration, and rate limiting (e.g., 5 login attempts per minute per IP).
- **Error Handling**: Log authentication failures, return clear error messages for invalid inputs.

## 2. Property Management
### Overview
Property Management allows Hosts to create and update property listings, including details like title, description, location, price, and amenities. Listings are stored in a relational database and accessible via RESTful APIs.

### API Endpoints
1. **Create Property Listing**
   - **Method**: POST
   - **URL**: `/api/v1/properties`
   - **Description**: Creates a new property listing for a Host.
   - **Authentication**: Requires JWT (Host role).
2. **Update Property Listing**
   - **Method**: PUT
   - **URL**: `/api/v1/properties/{property_id}`
   - **Description**: Updates an existing property listing.
   - **Authentication**: Requires JWT (Host role, must own the property).

### Input Specifications
- **Create Property Listing**:
  - **Request Body** (JSON):
    ```json
    {
      "title": "string",
      "description": "string",
      "location": "string",
      "price_per_night": "number",
      "amenities": ["string"]
    }
    ```
  - **Fields**:
    - `title`: Listing title (e.g., "Cozy Cottage").
    - `description`: Detailed description (max 1000 characters).
    - `location`: Address or city (e.g., "Nairobi, Kenya").
    - `price_per_night`: Price per night (positive number, e.g., 75.00).
    - `amenities`: Array of amenities (e.g., ["Wi-Fi", "Pool"]).
- **Update Property Listing**:
  - **Request Body** (JSON): Same as Create, but fields are optional.
  - **Path Parameter**:
    - `property_id`: Unique identifier of the property (string, UUID).

### Output Specifications
- **Create Property Listing**:
  - **Success Response** (201 Created):
    ```json
    {
      "status": "success",
      "message": "Property created successfully",
      "data": {
        "property_id": "string",
        "title": "string",
        "location": "string",
        "price_per_night": "number"
      }
    }
    ```
  - **Error Response** (401 Unauthorized):
    ```json
    {
      "status": "error",
      "message": "Unauthorized: Host role required"
    }
    ```
- **Update Property Listing**:
  - **Success Response** (200 OK):
    ```json
    {
      "status": "success",
      "message": "Property updated successfully",
      "data": {
        "property_id": "string",
        "title": "string",
        "location": "string",
        "price_per_night": "number"
      }
    }
    ```
  - **Error Response** (404 Not Found):
    ```json
    {
      "status": "error",
      "message": "Property not found"
    }
    ```

### Validation Rules
- **Create Property Listing**:
  - `title`: Required, max 100 characters, alphanumeric and spaces.
  - `description`: Required, max 1000 characters.
  - `location`: Required, max 200 characters, valid address format.
  - `price_per_night`: Required, positive number, max 10000.00, 2 decimal places.
  - `amenities`: Optional, array of strings, each max 50 characters.
- **Update Property Listing**:
  - All fields optional, same validation as Create when provided.
  - `property_id`: Valid UUID, exists in Properties table, owned by the authenticated Host.
- Authentication: JWT must be valid, with Host role.

### Performance Criteria
- **Response Time**: < 200 ms for create/update (under normal load).
- **Scalability**: Support 1,000 concurrent listing creations with database indexing.
- **Security**: Restrict updates to property owners, use HTTPS, and sanitize inputs to prevent SQL injection.
- **Error Handling**: Log invalid requests, return specific error messages for validation failures.

## 3. Booking System
### Overview
The Booking System enables Guests to create bookings for properties, ensuring availability and processing payments. It validates booking requests, stores booking data, and triggers notifications.

### API Endpoints
1. **Create Booking**
   - **Method**: POST
   - **URL**: `/api/v1/bookings`
   - **Description**: Creates a new booking for a property.
   - **Authentication**: Requires JWT (Guest role).

### Input Specifications
- **Create Booking**:
  - **Request Body** (JSON):
    ```json
    {
      "property_id": "string",
      "start_date": "string", // ISO 8601, e.g., "2025-06-01"
      "end_date": "string", // ISO 8601, e.g., "2025-06-03"
      "number_of_guests": "number",
      "payment_details": {
        "method": "string", // "credit_card", "paypal" "Stripe"
        "card_number": "string"
      }
    }
    ```
  - **Fields**:
    - `property_id`: Unique identifier of the property (UUID).
    - `start_date`: Booking start date (ISO 8601).
    - `end_date`: Booking end date (ISO 8601).
    - `number_of_guests`: Number of guests (positive integer).
    - `payment_details`: Payment method and details.

### Output Specifications
- **Create Booking**:
  - **Success Response** (201 Created):
    ```json
    {
      "status": "success",
      "message": "Booking created successfully",
      "data": {
        "booking_id": "string",
        "property_id": "string",
        "start_date": "string",
        "end_date": "string",
        "total_price": "number",
        "status": "confirmed"
      }
    }
    ```
  - **Error Response** (400 Bad Request):
    ```json
    {
      "status": "error",
      "message": "Dates unavailable or invalid"
    }
    ```

### Validation Rules
- **Create Booking**:
  - `property_id`: Required, valid UUID, exists in Properties table.
  - `start_date`: Required, valid ISO 8601 date, not in the past.
  - `end_date`: Required, valid ISO 8601 date, after `start_date`.
  - `number_of_guests`: Required, positive integer, within property's capacity (checked against Properties table).
  - `payment_details.method`: Required, must be "credit_card" or "paypal".
  - `payment_details.card_number`: Required for credit_card, valid format (simplified for example).
  - Availability: No overlapping bookings in Bookings table for the property and dates.
- Authentication: JWT must be valid, with Guest role.

### Performance Criteria
- **Response Time**: < 300 ms for booking creation (including payment processing).
- **Scalability**: Handle 5,000 concurrent booking requests with database locking for availability checks.
- **Security**: Use HTTPS, validate payment details via Payment Gateway, and ensure atomic transactions for booking and payment.
- **Error Handling**: Log booking failures, rollback transactions on payment errors, and return clear error messages.

