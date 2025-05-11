# Airbnb Clone Backend Flowchart

## Objective
This directory contains the documentation for Task 4 of the ALX Airbnb Clone project: designing a flowchart to map the workflow and processes of a key backend feature. The chosen process is the **property booking** process, which is central to the Airbnb Clone backend, involving steps such as searching properties, checking availability, submitting a booking request, processing payment, and sending notifications.

## Files
- **README.md**: This file, describing the purpose and contents of the flowchart.
- **flowchart.png**: A Draw.io flowchart visualizing the steps and data flow of the property booking process.

## Flowchart Overview
The `flowchart.png` illustrates the property booking process, a core backend operation in the Airbnb Clone system. This process allows a Guest to search for a property, check its availability, submit a booking request, process payment, and receive confirmation, while the system validates requests, creates booking records, and notifies both Guest and Host. The flowchart is based on the features from Task 0 (`features-and-functionalities/`), the use case “Create Booking” from Task 1 (`use-case-diagram/`), the user story “As a Guest, I want to create a booking…” from Task 2 (`user-stories/`), and the “Create/Cancel Booking” process from Task 3’s DFD (`data-flow-diagram/`).

### Process Description
The property booking process includes the following steps:
1. **Guest Searches for Property**: The Guest enters search criteria (e.g., location, dates, guests).
2. **System Retrieves Properties**: The system queries the Properties data store to return matching properties.
3. **Guest Selects Property**: The Guest chooses a property from the search results.
4. **Check Availability**: The system checks the Bookings data store to ensure the selected dates are available.
5. **Guest Submits Booking Request**: The Guest submits a booking request with details (e.g., dates, guests).
6. **Validate Booking Request**: The system validates the request (e.g., user authentication, date validity).
7. **Process Payment**: The system processes payment via a Payment Gateway and stores payment details.
8. **Confirm Payment**: The system confirms payment success or handles errors.
9. **Create Booking**: The system creates a booking record in the Bookings data store.
10. **Send Notifications**: The system sends booking confirmation notifications to the Guest and Host.
11. **Booking Complete**: The process ends with a confirmed booking.

### Flowchart Details
- **Symbols**:
  - **Oval**: Start/End (e.g., “Start Booking Process”, “Booking Complete”).
  - **Rectangle**: Process/Action (e.g., “Guest enters search criteria”, “System creates booking record”).
  - **Diamond**: Decision (e.g., “Are dates available?”, “Is payment successful?”).
  - **Arrow**: Sequence/Data flow (e.g., “Search criteria”, “Booking details”).
- **Data Flows**: Labeled arrows indicate inputs/outputs (e.g., “Search results”, “Payment confirmation”).


## Diagram
The flowchart is structured to show Guest and system interactions, validation points, and integration with external systems (e.g., Payment Gateway).

To view the flowchart:
1. Navigate to the `flowcharts/` directory in the `alx-airbnb-project-documentation` repository.
2. Open `flowchart.png` in an image viewer or browser.
