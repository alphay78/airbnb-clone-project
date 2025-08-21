# AirBnB Clone Project

## Overview
The AirBnB Clone Project is a backend-focused application designed to replicate core features of Airbnb, providing a robust and scalable platform for managing users, property listings, bookings, payments, and reviews. The project emphasizes best practices in backend development, database optimization, API design, and application security, enabling learners to build a real-world, production-ready system.

## Project Goals
- **User Management:** Secure registration, authentication, and profile management.  
- **Property Management:** Creation, update, retrieval, and deletion of property listings.  
- **Booking System:** Enable users to make, manage, and track bookings.  
- **Payment Processing:** Handle transactions and record payment details.  
- **Review System:** Allow users to post and manage property reviews.  
- **Data Optimization:** Implement indexing and caching for efficient data retrieval and performance.  


## Team Roles

- **Backend Developer:**  
  Responsible for implementing API endpoints, writing business logic, and ensuring the backend supports all core functionalities such as user management, property listings, bookings, payments, and reviews.

- **Database Administrator (DBA):**  
  Manages database design, schema creation, indexing, and optimizations to ensure efficient data storage and retrieval.

- **DevOps Engineer:**  
  Handles deployment, monitoring, scaling of backend services, and sets up CI/CD pipelines to automate testing and deployment processes.

- **QA Engineer:**  
  Ensures backend functionalities work as intended by performing rigorous testing, identifying bugs, and verifying that the application meets quality standards.

## Technology Stack

- **Django:** A high-level Python web framework used for building the backend and RESTful APIs. Provides rapid development and a clean, pragmatic design.  

- **Django REST Framework (DRF):** An extension of Django that simplifies the creation and management of RESTful APIs, including authentication, serialization, and CRUD operations.  

- **GraphQL:** A query language for APIs that allows clients to request exactly the data they need, providing flexibility and efficiency in retrieving backend data.  

- **PostgreSQL:** A powerful relational database system used to store and manage all project data, including users, properties, bookings, payments, and reviews.  

- **Celery:** A distributed task queue for handling asynchronous tasks such as sending notifications or processing payments in the background.  

- **Redis:** An in-memory data store used for caching frequently accessed data and managing session information to improve performance.  

- **Docker:** A containerization platform used to create consistent development and deployment environments for the backend services.  

- **CI/CD Pipelines (GitHub Actions):** Automated pipelines for testing, building, and deploying code changes efficiently while minimizing human error.

## Database Design

The AirBnB Clone project uses a relational database to manage users, properties, bookings, payments, and reviews efficiently.

### **Entities and Key Fields**

1. **Users**
   - `id` (Primary Key)
   - `username`
   - `email`
   - `password` (hashed)
   - `role` (guest, host, admin)  
   **Relationships:**  
   - A user can own multiple properties.  
   - A user can make multiple bookings.  
   - A user can post multiple reviews.

2. **Properties**
   - `id` (Primary Key)
   - `title`
   - `description`
   - `location`
   - `price_per_night`
   - `owner_id` (Foreign Key → Users)  
   **Relationships:**  
   - Each property belongs to one user (host).  
   - A property can have multiple bookings and reviews.

3. **Bookings**
   - `id` (Primary Key)
   - `user_id` (Foreign Key → Users)
   - `property_id` (Foreign Key → Properties)
   - `check_in_date`
   - `check_out_date`  
   **Relationships:**  
   - Each booking belongs to one user and one property.  
   - A booking can have one payment.

4. **Payments**
   - `id` (Primary Key)
   - `booking_id` (Foreign Key → Bookings)
   - `amount`
   - `payment_method`
   - `status` (paid, pending)  
   **Relationships:**  
   - Each payment is linked to exactly one booking.

5. **Reviews**
   - `id` (Primary Key)
   - `user_id` (Foreign Key → Users)
   - `property_id` (Foreign Key → Properties)
   - `rating` (1–5)
   - `comment`  
   **Relationships:**  
   - Each review is linked to one user and one property.

---

### **Entity Relationships Summary**
- A **User** can own multiple **Properties**, make multiple **Bookings**, and post multiple **Reviews**.  
- A **Property** belongs to a **User** and can have multiple **Bookings** and **Reviews**.  
- A **Booking** belongs to one **User** and one **Property**, and can have one **Payment**.  
- A **Payment** is associated with a single **Booking**.  
- A **Review** is linked to a single **User** and a single **Property**.


