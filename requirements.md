# Backend Requirement Specifications – Airbnb Clone

---

## 1 User Authentication

### Description:

Manages user sign-up, login, and session handling with role-based access (guest/host/admin).

### API Endpoints:

* `POST /api/auth/register` – Register new user
* `POST /api/auth/login` – Authenticate user and issue JWT
* `GET /api/users/me` – Retrieve authenticated user profile

### Input/Output:

#### Register:

* **Input:**

  ```json
  {
    "first_name": "John",
    "last_name": "Doe",
    "email": "john@example.com",
    "password": "SecurePass123",
    "role": "host"
  }
  ```
* **Output:**

  ```json
  {
    "user_id": "uuid",
    "email": "john@example.com",
    "token": "jwt_token"
  }
  ```

#### Login:

* **Input:**

  ```json
  {
    "email": "john@example.com",
    "password": "SecurePass123"
  }
  ```
* **Output:**

  ```json
  {
    "token": "jwt_token"
  }
  ```

### Validation Rules:

* Unique email
* Password minimum 8 characters
* Role must be one of: `guest`, `host`, `admin`

### Performance Criteria:

* Authentication response < 500ms
* Token expiry: 1 hour (with refresh support)

---

## 2 Property Management

### Description:

Allows hosts to create, update, and delete property listings.

### API Endpoints:

* `POST /api/properties/` – Create new property
* `PUT /api/properties/{id}` – Update property details
* `DELETE /api/properties/{id}` – Remove property
* `GET /api/properties/` – List all properties
* `GET /api/properties/{id}` – Get property by ID

### Input/Output:

#### Create:

* **Input:**

  ```json
  {
    "name": "Cozy Cabin",
    "description": "A peaceful cabin in the woods.",
    "location": "Nairobi, Kenya",
    "price_per_night": 100.00
  }
  ```
* **Output:**

  ```json
  {
    "property_id": "uuid",
    "created_at": "timestamp"
  }
  ```

### Validation Rules:

* Only users with role `host` can create/edit/delete properties
* `price_per_night` must be a positive decimal
* Max 5MB images (if uploading photos)

### Performance Criteria:

* List fetch with pagination ≤ 300ms
* Search/filter to return first 20 results ≤ 500ms

---

## 3 Booking System

### Description:

Handles property booking creation, validation, and cancellation.

### API Endpoints:

* `POST /api/bookings/` – Create a booking
* `GET /api/bookings/me` – View user’s bookings
* `DELETE /api/bookings/{id}` – Cancel booking

### Input/Output:

#### Create:

* **Input:**

  ```json
  {
    "property_id": "uuid",
    "start_date": "2025-06-10",
    "end_date": "2025-06-15"
  }
  ```
* **Output:**

  ```json
  {
    "booking_id": "uuid",
    "status": "pending",
    "total_price": 500.00
  }
  ```

### Validation Rules:

* No overlapping bookings
* Start date must be in the future
* Minimum 1 night stay

### Performance Criteria:

* Booking conflict checks < 200ms
* Cancel response < 300ms

---

## 4 Payments

### Description:

Handles secure payment processing for bookings, including charging guests and scheduling payouts to hosts.

### API Endpoints:

* `POST /api/payments/charge` – Process guest payment
* `GET /api/payments/{booking_id}` – Retrieve payment status/details for a booking
* `POST /api/payments/payout` – (Admin/cron) Trigger host payout

### Input/Output:

#### Guest Payment:

* **Input:**

  ```json
  {
    "booking_id": "uuid",
    "payment_method": "card",
    "currency": "USD"
  }
  ```
* **Output:**

  ```json
  {
    "payment_id": "uuid",
    "status": "success",
    "amount": 750.00,
    "transaction_date": "2025-06-01T12:00:00Z"
  }
  ```

#### Payout (to host):

* **Input:**

  ```json
  {
    "booking_id": "uuid"
  }
  ```
* **Output:**

  ```json
  {
    "payout_id": "uuid",
    "status": "processed"
  }
  ```

### Validation Rules:

* Only bookings with status `confirmed` can be charged.
* Payout is allowed only **after** stay completion.
* Must validate card/token through third-party service (e.g., Stripe API).
* Prevent duplicate charges for same booking.

### Security:

* Use HTTPS for all transactions
* Store payment tokens only, not raw card data (PCI-DSS compliant)

### Performance Criteria:

* Payment initiation and response ≤ 2 seconds
* 99.9% payment reliability (handle timeouts, retries)



