# Airbnb Clone Backend Data Flow Diagram

## Objective
This directory contains the documentation for Task 3 of the ALX Airbnb Clone project: designing a Data Flow Diagram (DFD) to illustrate how data moves through the Airbnb Clone backend system. The DFD maps data inputs, processes, and outputs for core backend operations involving key entities such as users, properties, bookings, and payments, as outlined in the project requirements.

## Files
- **README.md**: This file, describing the purpose and contents of the DFD.
- **data-flow.png**: A diagram visualizing the data flow within the Airbnb Clone backend system.

## Data Flow Diagram Overview
The `data-flow.png` is a Level-1 DFD that illustrates the flow of data between external entities, processes, and data stores in the Airbnb Clone backend. It is based on the features and functionalities documented in Task 0 (`features-and-functionalities/`) and the use cases from Task 1 (`use-case-diagram/`). The diagram covers core operations such as user registration, property listing management, booking creation, payment processing, and administrative tasks, showing how data is input, processed, stored, and output.

### External Entities
- **Guest**: Provides user data, booking requests, payments, and reviews.
- **Host**: Provides property listings, responds to bookings, and receives payouts.
- **Admin**: Manages users, listings, bookings, and payments.
- **Payment Gateway**: Processes payments and confirms payouts.

### Processes
- **1.0 Register/Login User**: Handles user registration and authentication.
- **2.0 Create/Update Property Listing**: Manages creation and updates of property listings.
- **3.0 Search Properties**: Processes search queries for properties.
- **4.0 Create/Cancel Booking**: Manages booking creation and cancellation.
- **5.0 Process Payment**: Handles payment processing and payouts.
- **6.0 Submit/Respond to Review**: Manages review submission and responses.
- **7.0 Send Notification**: Sends email or in-app notifications.
- **8.0 Manage System**: Admin tasks for managing users, listings, bookings, and payments.

### Data Stores
- **D1 Users**: Stores user data (e.g., email, password, profile).
- **D2 Properties**: Stores property data (e.g., title, price, location).
- **D3 Bookings**: Stores booking data (e.g., dates, status).
- **D4 Payments**: Stores payment data (e.g., amount, method).
- **D5 Reviews**: Stores review data (e.g., rating, comment).

### Data Flows
- **User Data**: Guest/Host to Register/Login User, stored in D1 Users.
- **Listing Details**: Host to Create/Update Property Listing, stored in D2 Properties.
- **Search Criteria/Results**: Guest to Search Properties, retrieves from D2 Properties.
- **Booking Request/Cancellation**: Guest/Host to Create/Cancel Booking, stored in D3 Bookings.
- **Payment Details/Confirmation**: Guest to Process Payment, interacts with Payment Gateway, stored in D4 Payments.
- **Review Data/Response**: Guest/Host to Submit/Respond to Review, stored in D5 Reviews.
- **Notifications**: From processes (e.g., Create Booking, Process Payment) to Send Notification, then to Guest/Host.
- **Management Requests**: Admin to Manage System, interacts with all data stores.

## Diagram
External entities are positioned on the edges, processes in the center, and data stores nearby, connected by labeled arrows indicating data movement.

To view the diagram:
1. Navigate to the `data-flow-diagram/` directory in the `alx-airbnb-project-documentation` repository.
2. Open `data-flow.png` in an image viewer or browser.
