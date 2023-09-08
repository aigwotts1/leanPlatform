# Session Management Spring Boot Project for Lean Platform Technologies
Successfully Created the Project with test coverage for logic and rest Apis i.e. Rescheduling, Cancellation and booking reccuring sessions.
I have added one more Api just to check which sessions are there i.e. get Api.


## Overview

The Session Management component is implemented as a REST API using the Spring Framework. It allows users to perform the following actions on sessions:

- **Book a Reccuring Session**: Users can book a recurring session by providing session details, including date and frequency.

- **Cancel a Session**: Users can cancel a session, but only if it's more than 12 hours before the session's start time.

- **Reschedule a Session**: Users can reschedule a session, but only if it's more than 4 hours before the new session time.

- **Get Sessions**: Users can retrieve a list of all sessions.

## API Endpoints

### Book a Session

**Endpoint:** POST `/session/book`

**Description:** Book a recurring session by providing session details.

**Request Body:**
```json
{
  "id": 0,
  "userId": 1,
  "mentorId": 1,
  "date": "2023-09-09T11:12:50.994Z",
  "bookedAt": "2023-09-08T11:12:50.994Z",
  "frequency": 1
}
```

**Response:**
- HTTP 200 OK: Session booked successfully on 2023-09-08T16:44:03.320099500 for user to attend at 2023-09-09T05:13:55.404 and frequency is 1 per month.


### Cancel a Session

**Endpoint:** DELETE `/session/cancel/{sessionId}`

**Description:** Cancel a session by providing the session's unique identifier (`sessionId`). The session can be canceled only if it's more than 12 hours before the session's start time.

**Response:**
- HTTP 200 OK: Session canceled successfully.
- HTTP 400 Bad Request: Session cannot be canceled within 12 hours of the session time.
- HTTP 404 Not Found: No session found with the specified ID.

### Reschedule a Session

**Endpoint:** PUT `/session/reschedule/{sessionId}`

**Description:** Reschedule a session by providing the session's unique identifier (`sessionId`) and the new session details.

**Request Body:**
```json
{
  "id": 0,
  "userId": 1,
  "mentorId": 1,
  "date": "2023-09-08T11:12:50.994Z",
  "bookedAt": "2023-09-08T11:12:50.994Z",
  "frequency": 1
}
```

**Response:**
- HTTP 200 OK: Session rescheduled successfully.
- HTTP 400 Bad Request: Session cannot be rescheduled within 4 hours of the new session time.
- HTTP 404 Not Found: No session found with the specified ID.

### Get Sessions

**Endpoint:** GET `/session`

**Description:** Retrieve a list of all sessions.

**Response:**
- HTTP 202 Accepted: List of sessions in the response body.

## Exception Handling

- The API handles exceptions and returns appropriate error messages when sessions cannot be booked, canceled, or rescheduled.

## Dependencies

This component relies on the following dependencies:

- Spring Boot
- Spring Data JPA
- Spring Web
- H2 Database (for testing and development)
- Valid
- Swagger
- lombok

## Usage

To use this Session Management component, you can make HTTP requests to the provided API endpoints. Ensure that you have the required session details when booking, canceling, or rescheduling sessions.


#Hope this fulfills all the requirements, looking forward for next Steps.
Thank You,
Abhinav Vashishth
