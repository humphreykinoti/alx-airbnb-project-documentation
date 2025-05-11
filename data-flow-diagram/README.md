## Data Flow Diagram (DFD) for Airbnb Clone backend


### 🔄 1. **User Management**

Handles all user-related operations including registration, authentication, and profile management.

* **Inputs:**

  * User registration data (name, email, password, role)
  * Login credentials
  * Profile update requests

* **Processes:**

  * Validate input data
  * Store new users in the `Users` table
  * Generate JWT token for successful login
  * Update user profile information

* **Outputs:**

  * JWT token on successful login
  * User profile details

* **Data Store:**

  * `Users`

---

### 🏠 2. **Property Management**

Manages property listings created and edited by hosts.

* **Inputs:**

  * New property data (title, description, location, price, host ID)
  * Property update or delete requests

* **Processes:**

  * Validate host ownership
  * Insert or update property records
  * Retrieve listings for search or display

* **Outputs:**

  * Confirmation of property creation/update
  * List of properties based on search criteria

* **Data Store:**

  * `Properties`

---

### 📅 3. **Booking Management**

Allows guests to book available properties and manage booking status.

* **Inputs:**

  * Selected property ID
  * Booking dates
  * User ID (guest)

* **Processes:**

  * Check for property availability (date conflicts)
  * Insert booking record with status (e.g., pending)
  * Allow cancellation or status update

* **Outputs:**

  * Booking confirmation or error message
  * Updated booking status (confirmed, canceled)

* **Data Store:**

  * `Bookings`

---

### 💳 4. **Payment Processing**

Handles guest payments and payouts to hosts via external gateways.

* **Inputs:**

  * Booking ID
  * Payment method
  * Payment amount

* **Processes:**

  * Send payment request to external gateway (e.g., Stripe)
  * Record payment result
  * Trigger host payout after booking completion

* **Outputs:**

  * Payment receipt
  * Payout confirmation

* **Data Store:**

  * `Payments`

* **External Entity:**

  * `Payment Gateway`

---

### 🌟 5. **Review System**

Allows users to leave reviews and ratings for properties they've booked.

* **Inputs:**

  * Booking ID
  * Rating (1–5), comment
  * Reviewer ID

* **Processes:**

  * Validate that booking was completed
  * Store review linked to property and user

* **Outputs:**

  * Review confirmation
  * Displayed reviews for properties

* **Data Store:**

  * `Reviews`

---

### 🔔 6. **Notification Service**

Sends notifications to users for important events.

* **Inputs:**

  * Events (e.g., booking confirmed, payment made, property updated)

* **Processes:**

  * Format messages
  * Send emails via an external service (e.g., SendGrid)

* **Outputs:**

  * Email or in-app notifications

* **External Entity:**

  * `Email Service`

