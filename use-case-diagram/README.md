# Airbnb Clone Backend Use Case Diagram

## Objective
This directory contains the documentation for Task 1 of the ALX Airbnb Clone project: designing a use case diagram to visualize the interactions between users and the Airbnb Clone backend system. The diagram captures how key actors (Guest, Host, Admin) interact with core functionalities such as user registration, property booking, and payments, as outlined in the project requirements.

## Files
- **README.md**: This file, describing the use case diagram and its purpose.
- **use-case-diagram.png**: A Draw.io diagram visualizing the actors, use cases, and their interactions within the Airbnb Clone backend system.

## Use Case Diagram Overview
The `use-case-diagram.png` illustrates the interactions between three primary actors (Guest, Host, Admin) and the Airbnb Clone backend system. It is based on the features and functionalities documented in Task 0 (`features-and-functionalities/`), including User Management, Property Listings Management, Booking Management, Payment Integration, Reviews and Ratings, Notifications System, and Admin Dashboard. The diagram uses UML notation to show associations, includes, and extends relationships, providing a clear view of how users engage with the system.

### Actors
- **Guest**: A user who searches for properties, makes bookings, processes payments, submits reviews, and receives notifications.
- **Host**: A user who creates and manages property listings, responds to reviews, receives payouts, and manages bookings.
- **Admin**: A user who manages users, listings, bookings, and payments through an admin dashboard.

### Use Cases
The use cases, grouped by functionality, are:
1. **User Management**:
   - Register Account: Guests and Hosts sign up.
   - Login: Guests, Hosts, and Admins authenticate.
   - Update Profile: Guests and Hosts edit their profiles.
2. **Property Listings Management**:
   - Create Listing: Hosts add new properties.
   - Edit/Delete Listing: Hosts update or remove properties.
3. **Search and Filtering**:
   - Search Properties: Guests search by location, price, etc.
4. **Booking Management**:
   - Create Booking: Guests book properties.
   - Cancel Booking: Guests or Hosts cancel bookings.
   - View Booking Status: Guests and Hosts track booking status.
5. **Payment Integration**:
   - Process Payment: Guests make payments.
   - Receive Payout: Hosts receive payments.
6. **Reviews and Ratings**:
   - Submit Review: Guests leave reviews for properties.
   - Respond to Review: Hosts reply to guest reviews.
7. **Notifications System**:
   - Receive Notification: Guests and Hosts get updates (e.g., booking confirmations).
8. **Admin Dashboard**:
   - Manage Users: Admins oversee user accounts.
   - Manage Listings: Admins monitor property listings.
   - Manage Bookings: Admins handle booking issues.
   - Manage Payments: Admins track payment transactions.

### Relationships
- **Associations**: Solid lines connect actors to use cases (e.g., Guest to Create Booking).
- **Includes**: Dashed lines with `<<include>>` indicate required actions (e.g., Create Booking includes Process Payment).
- **Extends**: Dashed lines with `<<extend>>` show optional actions (e.g., Search Properties may extend to Create Booking).

## Diagram
The `use-case-diagram.png`, created using Draw.io, visualizes the actors, use cases, and relationships within the Airbnb Clone system. Actors are positioned outside a system boundary, with use cases inside, connected by associations, includes, and extends relationships. The diagram is color-coded for clarity (e.g., blue for Guest, green for Host, orange for Admin) and includes a title and legend.

To view the diagram:
1. Navigate to the `use-case-diagram/` directory in the `alx-airbnb-project-documentation` repository.
2. Open `use-case-diagram.png` in an image viewer or browser.
