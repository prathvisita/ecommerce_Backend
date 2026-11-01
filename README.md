# E-Commerce Backend API

A robust, production-ready backend system for an online retail platform built using **Java, Spring Boot, and MySQL**. This application provides a scalable RESTful API handling everything from secure authentication and user profiles to product catalogs, shopping carts, checkout workflows, and payment gateway simulations.

---

## 🚀 Key Features

*   **Secure Authentication:** Token-based security implementing JWT (JSON Web Tokens) with distinct Role-Based Access Control (RBAC) for Customers, Sellers, and Admins.
*   **Product & Catalog Management:** Full CRUD operations supporting category filtering, product inventory tracking, pagination, and sorting.
*   **Shopping Cart & Wishlist:** Dynamic cart handling, real-time quantity validation, and session state persistence.
*   **Order & Checkout Workflow:** Secure order processing, automated stock validation, unique order tracking generation, and payment gateway mock integration.
*   **Data Consistency & Transacting:** Database schema tracking using structural migration tools with clear transactional boundaries (`@Transactional`).

---

## 🛠️ Tech Stack & Dependencies

*   **Language:** Java 21 / 17
*   **Framework:** Spring Boot 3.x (Spring Web, Spring Security, Spring Data JPA)
*   **Database:** MySQL 8.x / PostgreSQL
*   **Build Tool:** Maven
*   **Libraries:** Lombok (boilerplate reduction), MapStruct (DTO-to-Entity mapping), Validation API

---

## 📁 Project Architecture

The project follows a modular, feature-by-layer structure optimizing separation of concerns:

```text
src/main/java/com/example/ecommerce
│
├── config/             # Security, JWT, CORS, and App configurations
├── controller/         # REST API Controllers (Exposes endpoints)
├── dto/                # Data Transfer Objects for request/response payloads
├── exception/          # Global Exception Handler and custom exceptions
├── model/              # JPA Database Entities
├── repository/         # Spring Data JPA Repositories (Data access layer)
└── service/            # Core Business Logic and implementations
```

---

## ⚙️ Getting Started

### Prerequisites
*   **JDK 17** or higher installed
*   **Maven 3.x** installed
*   **MySQL Server** running locally or via Docker

### 1. Database Configuration
Create a database named `ecommerce_db` in your SQL client. Update your `src/main/resources/application.yml` or `application.properties` with your credentials:

```yaml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/ecommerce_db?useSSL=false&serverTimezone=UTC
    username: your_db_username
    password: your_db_password
  jpa:
    hibernate:
      ddl-auto: validate
    show-sql: true
```

### 2. Build and Run
Navigate to the project root directory and execute the following commands:

```bash
# Clone the repository
git clone https://github.com
cd ecommerce-backend

# Clean and build the application
./mvnw clean install

# Spin up the Spring Boot application
./mvnw spring-boot:run
```
The application will bootstrap by default on port `8080`.

---

## 🔌 API Endpoints Summary

### Auth & User Management
*   `POST /api/auth/register` - Create a new customer or seller account.
*   `POST /api/auth/login` - Authenticate user and receive a JWT Bearer token.
*   `GET /api/users/profile` - Fetch current authenticated user's details.

### Product Catalog
*   `GET /api/products` - Retrieve list of products (Supports pagination parameters: `page`, `size`, `sortBy`).
*   `GET /api/products/{id}` - Fetch a specific product by ID.
*   `POST /api/products` - Add a new product *(Sellers/Admins only)*.

### Cart & Orders
*   `GET /api/cart` - View items inside the active user's shopping cart.
*   `POST /api/cart/add` - Add items or increment product quantity in the cart.
*   `POST /api/orders/checkout` - Convert cart items into an active order, compute totals, and trigger payment simulation.
*   `GET /api/orders/history` - Fetch previous order transactions for the current user.

---

## 🧪 Running Tests
This project includes unit and integration tests using JUnit 5 and Mockito. To execute the test suite, run:

```bash
./mvnw test
```
