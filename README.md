# Event Management System

## Objective

Develop a simple Event Management System using **PHP (OOP)**, **MySQL**, and a frontend framework of your choice. The system should allow the following functionalities:

1. **Event Management**:

    - Add new events (optional).
    - List all events.
    - Get details for a specific event.

2. **User Registration for Events**:

    - Register a user for an event.

## Requirements

- Use **PHP 7.4+** (preferably PHP 8) with **OOP principles**.
- Use **MySQL** for the database.
- Implement a frontend using any framework (e.g., React, Vue.js, Angular) and a UI library.
- APIs should return responses in JSON format.
- Ensure proper validation and error handling.

---

## Features

### 1. **Frontend Functionality**

- **List All Events**:
    - Display a list of events, including the name, description, date, and image.
    - Each event should have a "View Details" button.

- **Event Details**:
    - Show event details in a modal or a separate page when "View Details" is clicked.
    - Include the event name, description, date, and image.
    - Provide a registration form for the event in the details view.

- **Registration Form**:
    - Fields: `User Name`, `Email`.
    - On successful registration, display a confirmation message.

### 2. **Event Management**

- **Add Event (Optional)**:

    - Endpoint: `POST /events`
    - Request Body:
      ```json
      {
        "name": "Event Name",
        "description": "Event Description",
        "date": "YYYY-MM-DD HH:MM:SS",
        "image": "image_url"
      }
      ```
    - Response:
        - Success: `{ "message": "Event created successfully" }`
        - Failure: `{ "error": "Validation error or database error" }`

  Example PHP array for data:

  if you want to add some events to the database, you can use the following array to insert the data into the database.
  ```php
  $eventData = [
      [
          'name' => 'Music Concert',
          'description' => 'An exciting music event.',
          'date' => '2024-12-25 18:00:00',
          'image' => 'https://picsum.photos/1000/300'
      ],
      [
          'name' => 'Art Exhibition',
          'description' => 'Explore amazing art pieces.',
          'date' => '2024-12-30 10:00:00',
          'image' => 'https://picsum.photos/1000/300'
      ]
  ];
  ```

- **List Events**:

    - Endpoint: `GET /events`
    - Response:
      ```json
      [
        {
          "id": 1,
          "name": "Event Name",
          "description": "Event Description",
          "date": "YYYY-MM-DD HH:MM:SS",
          "image": "image_url"
        }
      ]
      ```

- **Get Event Details**:

    - Endpoint: `GET /events/:id`
    - Response:
      ```json
      {
        "id": 1,
        "name": "Event Name",
        "description": "Event Description",
        "date": "YYYY-MM-DD HH:MM:SS",
        "image": "image_url"
      }
      ```

### 3. **User Registration for Events**

- **Register User**:
    - Endpoint: `POST /registrations`
    - Request Body:
      ```json
      {
        "event_id": 1,
        "user_name": "John Doe",
        "email": "john@example.com"
      }
      ```
    - Response:
        - Success: `{ "message": "User registered successfully" }`
        - Failure: `{ "error": "Validation error" }`

---

## Database Schema

```sql
CREATE TABLE events
(
    id          INT AUTO_INCREMENT PRIMARY KEY,
    name        VARCHAR(255) NOT NULL,
    description TEXT,
    date        DATETIME     NOT NULL,
    image       VARCHAR(255) NOT NULL,
    created_at  TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE registrations
(
    id            INT AUTO_INCREMENT PRIMARY KEY,
    event_id      INT          NOT NULL,
    user_name     VARCHAR(255) NOT NULL,
    email         VARCHAR(255) NOT NULL,
    registered_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (event_id) REFERENCES events (id)
);
```
---

## Deliverables

- Source code for both backend and frontend.
- README file with instructions on how to run and test the system.

---

Good luck! If you have any questions, feel free to ask.

