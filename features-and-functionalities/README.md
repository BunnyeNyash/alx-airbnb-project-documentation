# Features and Functionalities Documentation

## Objective
This directory contains the documentation for Task 0 of the ALX Airbnb Clone project: identifying and documenting the key features and functionalities of the Airbnb Clone backend. The goal is to outline the technical and functional requirements necessary for building a scalable, secure, and robust rental marketplace backend.

## Files
- **README.md**: This file, summarizing the backend features and functionalities.
- **features-and-functionalities.png**: A Draw.io diagram visualizing the core functionalities, technical requirements, and non-functional requirements of the Airbnb Clone backend.

## Features and Functionalities
The features and functionalities are categorized into Core Functionalities, Technical Requirements, and Non-Functional Requirements, as detailed below and visualized in `features-and-functionalities.png`.

### Core Functionalities
1. **User Management**:
   - User registration with email, password, first name, last name, and optional phone number, using secure authentication (e.g., JWT).
   - User login with email/password and OAuth (e.g., Google)
   - Role-based access control (guest, host, admin).
   - Password hashing for security.
   - Account management (update profile details including photos, contact info, and preferences, change password).

2. **Property Management**:
   - Hosts can create property listings with details like title, description, location, price per night, amenities, and availability.
    - Hosts can update or delete property listings.

3. **Search and Filtering**:
   - Users can search properties by location, price range, number of guests, and amenities (e.g., Wi-Fi, pool).
   - Includes pagination for efficient handling of large datasets.

4. **Booking Management**:
   - Guests can book properties for specific dates, with validation to prevent double bookings.
   - Booking creation with start date, end date, and total price calculation.
   - Supports cancellations by guests or hosts based on policies.
   - Tracks booking statuses (pending, confirmed, canceled, completed).

5. **Payments**:
  - Guests can make payments for bookings via multiple methods (credit card, PayPal, Stripe).
  - Secure payment gateways for guest payments and host payouts.
  - Payment recording with amount, date, and method.
  - Supports multiple currencies
  - Support for partial or multiple payments for a single booking.
  - Payment validation to ensure amounts match booking totals.
     
6. **Reviews and Ratings**:
   - Guests can leave reviews and ratings (1-5 rating + comment) for properties, linked to specific bookings.
   - Display of reviews for properties to assist guest decision-making.
   - Hosts can respond to reviews.

7. **Notifications System**:
   - Sends email and in-app notifications for booking confirmations, cancellations, and payment updates.
     
8. **Admin Dashboard**:
   - Provides an interface for admins to manage users, listings, bookings, and payments.



### Technical Requirements
- **Database**: MySQL with tables for users, listings, bookings, reviews, payments
- **APIs**: RESTful APIs with proper HTTP methods (GET, POST, PUT/PATCH, DELETE) and status codes. GraphQL for complex data fetching (optional)
- **Authentication**: JWT-based with role-based access control (RBAC) for guests, hosts, and admins
- **Storage**: AWS S3 or Cloudinary for image storage (property images, profile photos)
- **Email**: SendGrid or Mailgun for notification services
- **Error Handling & Logging**: Global API error handling and logs for debugging.



### Non-Functional Requirements
- **Scalability**: Modular architecture and load balancers for horizontal scaling
- **Security**: Data encryption, firewalls, rate limiting
- **Performance**: Redis caching and query optimization
- **Testing**: Unit, integration, and API tests using pytest

## Diagram
The `features-and-functionalities.png` file, visually organizes the backend features into three categories: Core Functionalities, Technical Requirements, and Non-Functional Requirements. Each category is broken down into specific features (e.g., User Management → Registration, Login, Profile).


To view the diagram:
1. Navigate to the `features-and-functionalities/` directory in the `alx-airbnb-project-documentation` repository.
2. Open `features-and-functionalities.png` in an image viewer or browser.












