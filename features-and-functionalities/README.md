# 🏠 Airbnb Clone Backend – Features & Functionalities

## 🎯 Objective
This backend system powers the core functionalities of an Airbnb-like rental marketplace, offering support for property listings, user roles, bookings, payments, reviews, and more — all built with scalability and security in mind.

---

## 🔑 Core Functionalities

### 1. 👤 User Management
- **Registration**: Guests and Hosts can sign up.
- **Authentication**: Secure login via email/password with JWT.
- **OAuth Login**: Social login support (Google, Facebook).
- **Profile Management**: Update profile info, photo, and role.
- **Role Support**: Differentiates between Guest, Host, Admin.

### 2. 🏡 Property Listings Management
- **Create Listing**: Hosts can add property details including price, location, description, and amenities.
- **Edit/Delete Listing**: Listings can be modified or removed by the host.
- **File Upload**: Support for uploading property images.

### 3. 🔍 Search and Filtering
- Search properties by:
  - Location
  - Price range
  - Number of guests
  - Amenities (Wi-Fi, pool, pet-friendly)
- Pagination support for large result sets.

### 4. 📅 Booking Management
- **Book Property**: Guests can make bookings for available dates.
- **Date Validation**: Prevent double bookings.
- **Booking Cancellation**: Available to both guests and hosts.
- **Booking Status Tracking**: `pending`, `confirmed`, `canceled`.

### 5. 💳 Payment Integration
- **Secure Payments**: Stripe, PayPal integration.
- **Guest Payments**: Collected upfront.
- **Host Payouts**: Automated payouts post-booking.
- **Multi-Currency Support**: Future-ready payment design.

### 6. ⭐ Reviews and Ratings
- **Guest Reviews**: Tied to confirmed bookings.
- **Host Responses**: Hosts can reply to feedback.
- **Rating System**: 1–5 stars with comment support.

### 7. 🔔 Notification System
- **Email & In-App Notifications** for:
  - Booking confirmations
  - Payment status
  - Cancellations and updates

### 8. 🧑‍💼 Admin Dashboard
- **User Management**: View or disable users.
- **Listings Oversight**: Monitor active listings.
- **Booking & Payment Monitoring**: Admin-level insights.


- Prepared for future integrations such as GraphQL and cloud deployment.

---

