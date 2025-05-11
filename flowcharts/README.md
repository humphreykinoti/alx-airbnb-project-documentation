# 📘 Backend Process Workflows – Airbnb Clone

This document outlines the key system workflows for two core backend features: **User Registration** and **Property Booking**. These processes ensure secure account creation and efficient booking management in the Airbnb Clone application.

---

## 🔐 User Registration Workflow

The user registration process allows individuals to create an account as either a guest or a host.

### Steps:

1. User accesses the registration page.
2. Enters required information (name, email, password, phone, role).
3. Backend validates input and checks for duplicate emails.
4. Password is securely hashed.
5. A unique `user_id` is generated.
6. User data is stored in the database.
7. A JWT token is generated for authentication.
8. A success response is returned.

---

## 🏠 Property Booking Workflow

The booking process allows guests to reserve available properties for specific dates.

### Steps:

1. Logged-in user views property listings and selects a property.
2. Selects desired check-in and check-out dates.
3. Backend checks availability (no overlapping bookings).
4. Total booking price is calculated.
5. A new booking record is created with `pending` status.
6. User is redirected to the payment gateway.
7. On successful payment, the `payments` table is updated.
8. Booking status is updated to `confirmed`.
9. Notifications are sent to the guest and host.

---

These workflows are foundational to the user experience and system reliability of the Airbnb Clone backend.

