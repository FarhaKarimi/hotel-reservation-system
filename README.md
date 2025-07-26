Hotel Room Booking Microservices Project
Overview
This project implements a modular, microservices-based hotel room booking system using Spring Boot. It consists of five independent services communicating via REST APIs and event-driven architecture for scalability, maintainability, and clear separation of concerns.

Services
1. User Service
Handles user registration, login, and authentication.

Uses JWT for secure stateless auth.

Maintains its own database for user info.

2. Room Service
Manages hotel room inventory: types, availability, pricing, features.

Exposes APIs to query room availability and details.

Keeps real-time room status updated.

3. Booking Service
Responsible for managing bookings lifecycle: create, update, cancel.

Locks rooms during booking to prevent double-booking.

Tracks booking statuses: Pending, Confirmed, Cancelled.

Coordinates with Room Service to ensure availability.

4. Payment Service
Handles payment transactions for bookings.

Integrates with external payment gateways.

Updates booking status upon successful payment.

5. Notification Service
Sends email/SMS notifications for booking events (confirmation, cancellation, reminders).

Listens to events from other services (event-driven).

Architecture & Tech
Microservices deployed independently, each with own database (DB per service pattern).

Communication via REST APIs and asynchronous events (event-driven architecture).

Authentication & authorization using JWT tokens.

Containerized using Docker; orchestration with Docker Compose.

Tests include unit, integration, and end-to-end tests to ensure quality.

Clean Architecture principles and Separation of Concerns strictly followed.

API Examples
User Service
POST /users/register - Register new user

POST /users/login - Authenticate user, get JWT

Room Service
GET /rooms - List all rooms

GET /rooms/{id} - Get room details

Booking Service
POST /bookings - Create a booking

DELETE /bookings/{id} - Cancel a booking

Payment Service
POST /payments - Process payment

Getting Started
Prerequisites
Java 17+

Docker & Docker Compose

Maven

Running Locally
Clone the repo

Build each service:

bash
Copy
Edit
cd user-service && mvn clean install  
cd ../room-service && mvn clean install  
# repeat for all services  
Start services with Docker Compose:

bash
Copy
Edit
docker-compose up --build  
Testing
Unit and integration tests included in each module.

Run tests with Maven:
