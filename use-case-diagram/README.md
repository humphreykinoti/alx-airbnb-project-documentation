# 🏠 Airbnb Clone Backend – Requirements


## 🛠️ Technical Requirements

- **Database**: PostgreSQL
- **API**: RESTful design using HTTP verbs and status codes
- **Authentication**: JWT-based, Role-based Access Control (RBAC)
- **File Uploads**: Support for profile and property images
- **Email Services**: Integrated with SendGrid or Mailgun
- **Error Handling**: Centralized and consistent across endpoints

---

## 🚀 Non-Functional Requirements

- **Scalability**: Horizontal scaling with modular code structure
- **Security**:
  - Password hashing and encryption
  - Rate limiting & input validation
- **Performance**:
  - Redis for caching search data
  - Optimized DB queries
- **Testing**:
  - Unit and integration testing (pytest)
  - Automated endpoint validation

---

## 📌 Notes
- Built with extensibility and real-world scenarios in mind.
- All endpoints follow standard REST conventions.
- Prepared for future integrations such as GraphQL and cloud deployment.

---

