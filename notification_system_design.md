# Notification System Design

## Overview
This project is a frontend-based notification system that allows users to create and view notifications. The system is designed with a focus on modularity, usability, and graceful error handling.

---

## Architecture
The application follows a component-based architecture using React, with clear separation of concerns:

- **Components**
  - `NotificationForm` → Handles user input and creation of notifications
  - `NotificationList` → Displays notifications with sorting and filtering

- **Services**
  - `api.js` → Handles API communication
  - `auth.js` → Manages authentication (register + token)
  
- **Middleware**
  - `logger.js` → Sends logs to backend service

---

## Data Flow
1. User enters a notification in the form
2. Form updates UI instantly using local state
3. API call is triggered to send data to backend
4. If API fails, fallback logic ensures UI remains functional
5. Notifications are displayed in the list component

---

## Features

### 1. Notification Creation
- Users can create notifications with:
  - Type (Placement / Event / Result)
  - Message
  - Timestamp (auto-generated)

### 2. Real-time UI Update
- Notifications are added instantly without waiting for API response

### 3. Sorting Logic
- Notifications are sorted based on priority:
  - Placement > Event > Result
- Within same type, sorted by latest timestamp

### 4. Filtering
- Users can filter notifications by:
  - All
  - Placement
  - Event
  - Result

### 5. Error Handling
- API failures are handled gracefully
- Fallback data ensures UI remains usable

### 6. Logging
- Logs are sent for:
  - API calls
  - Errors
  - Component actions

---

## API Integration
- POST `/notifications` → Send notification
- GET `/notifications` → Fetch notifications
- POST `/auth` → Get token
- POST `/register` → Register client

---

## State Management
- Managed using React `useState`
- Notifications stored in parent (`App.jsx`)
- Passed as props to child components

---

## UI Design
- Clean and minimal interface
- Card-based notification display
- Color-coded types:
  - Placement → Green
  - Event → Blue
  - Result → Orange

---

## Reliability Considerations
- Fallback mechanism for API failure
- Token stored in localStorage
- Safe logging (non-blocking)

---

## Conclusion
The system is designed to be modular, resilient, and user-friendly. It ensures smooth user experience even in case of backend issues, while maintaining clean architecture and scalable design.
