# airbnb-clone-project

Team Roles:

Backend Developer: Responsible for implementing API endpoints, database schemas, and business logic.
Database Administrator: Manages database design, indexing, and optimizations.
DevOps Engineer: Handles deployment, monitoring, and scaling of the backend services.
QA Engineer: Ensures the backend functionalities are thoroughly tested and meet quality standards.

Technology Stack:

Django: A high-level Python web framework used for building the RESTful API.
Django REST Framework: Provides tools for creating and managing RESTful APIs.
PostgreSQL: A powerful relational database used for data storage.
GraphQL: Allows for flexible and efficient querying of data.
Celery: For handling asynchronous tasks such as sending notifications or processing payments.
Redis: Used for caching and session management.
Docker: Containerization tool for consistent development and deployment environments.
CI/CD Pipelines: Automated pipelines for testing and deploying code changes.

Database Design:
1. Users
Description: Represents both guests and hosts on the platform.
Key Fields:
id: Primary key, unique identifier.
username: Unique name for user login.
email: User's email address.
password_hash: Securely stored password.
is_host: Boolean flag indicating if the user can list properties.
Relationships:
A user can list multiple properties (One-to-Many).
A user can make multiple bookings (One-to-Many).
A user can leave multiple reviews (One-to-Many).

2. Properties
Description: Represents homes or rooms listed by hosts for booking.
Key Fields:
id: Primary key.
owner_id: Foreign key linking to Users.
title: Name of the property.
description: Property details.
location: Address or general area of the property.
price_per_night: Cost to book per night.
Relationships:
A property belongs to one user (Many-to-One).
A property can have many bookings (One-to-Many).
A property can have many reviews (One-to-Many).

3. Bookings
Description: Represents reservations made by users for specific properties.
Key Fields:
id: Primary key.
user_id: Foreign key referencing Users (guest).
property_id: Foreign key referencing Properties.
check_in: Start date of the booking.
check_out: End date of the booking.
status: Booking status (e.g., confirmed, canceled).
Relationships:
Each booking is made by one user (Many-to-One).
Each booking is for one property (Many-to-One).
Each booking can have one associated payment (One-to-One).

4. Payments
Description: Records financial transactions related to bookings.
Key Fields:
id: Primary key.
booking_id: Foreign key referencing Bookings.
amount: Payment total.
payment_method: Method used (e.g., credit card, PayPal).
status: Payment status (e.g., paid, failed).
Relationships:
A payment is linked to one booking (One-to-One).

5. Reviews
Description: Feedback left by users about properties they have stayed in.
Key Fields:
id: Primary key.
user_id: Foreign key referencing Users.
property_id: Foreign key referencing Properties.
rating: Score (e.g., 1 to 5 stars).
comment: Textual feedback.
Relationships:
A review is written by one user (Many-to-One).
A review is for one property (Many-to-One).


