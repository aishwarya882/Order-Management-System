#  📦 Order-Management-System
Order Management System backend built using Spring Boot, REST APIs, and Postgres.

A **RESTful Order Management System** built using **Spring Boot**, following **clean architecture**, **DTO–Mapper pattern**, and **best backend practices**.

This application allows you to manage:

* Customers
* Products
* Orders
* Order Items
  with full **CRUD operations**, **business validations**, and **transaction safety**.

---

## 🚀 Tech Stack

* **Java 17**
* **Spring Boot**
* **Spring Data JPA**
* **Hibernate**
* **REST APIs**
* **DTO & Mapper Pattern**
* **Postgres** (configurable)
* **Maven**

---

## 🏗️ Architecture Overview

```
Controller  →  Service  →  Repository
    ↓            ↓
   DTO  ←→  Mapper  ←→  Entity
```

### Why this design?

* ✅ Clean separation of concerns
* ✅ Secure API responses
* ✅ Avoids exposing JPA entities
* ✅ Easy to scale and maintain

---

## 📁 Project Structure

```
src/main/java/com/oms/ordermanagement
│
├── controller
│   ├── CustomerController
│   ├── ProductController
│   └── OrderController
│
├── service
│   ├── CustomerService
│   ├── ProductService
│   └── OrderService
│
├── repository
│   ├── CustomerRepository
│   ├── ProductRepository
│   ├── OrderRepository
│   └── OrderItemRepository
│
├── entity
│   ├── Customer
│   ├── Product
│   ├── Order
│   └── OrderItem
│
├── dto
│   ├── CustomerRequestDTO
│   ├── CustomerResponseDTO
│   ├── ProductRequestDTO
│   ├── ProductResponseDTO
│   ├── OrderRequest
│   ├── ModifyOrderRequest
│   └── OrderItemRequest
│
├── mapper
│   ├── CustomerMapper
│   └── ProductMapper
│
├── exception
│   ├── ResourceNotFoundException
│   ├── BusinessException
│   └── BadRequestException
│
└── OrderManagementApplication.java
```

---

## 🔄 DTO & Mapper Pattern

### Why DTOs?

* Prevent exposing internal database structure
* Control API input/output
* Improve security and flexibility

### Example Mapping

```java
// DTO → Entity
Product product = ProductMapper.toEntity(productRequestDTO);

// Entity → DTO
ProductResponseDTO response = ProductMapper.toDTO(product);
```

---

## 🧑‍💼 Customer APIs

| Method | Endpoint                                   | Description         |
| ------ | ------------------------------------------ | ------------------- |
| POST   | `/api/customers`                           | Create customer     |
| GET    | `/api/customers/by-id?customerId=1`        | Get customer        |
| GET    | `/api/customers`                           | Get all customers   |
| PUT    | `/api/customers?customerId=1`              | Update customer     |
| DELETE | `/api/customers?customerId=1`              | Delete customer     |
| GET    | `/api/customers/orders?customerId=1`       | Get customer orders |
| GET    | `/api/customers/orders/items?customerId=1` | Get order items     |

---

## 📦 Product APIs

| Method | Endpoint                          | Description      |
| ------ | --------------------------------- | ---------------- |
| POST   | `/api/products`                   | Create product   |
| GET    | `/api/products/by-id?productId=1` | Get product      |
| GET    | `/api/products?sortBy=name`       | Get all products |
| PUT    | `/api/products?productId=1`       | Update product   |
| DELETE | `/api/products?productId=1`       | Delete product   |

---

## 🛒 Order APIs

| Method | Endpoint                       | Description              |
| ------ | ------------------------------ | ------------------------ |
| POST   | `/api/orders`                  | Place order              |
| GET    | `/api/orders/by-id?orderId=1`  | Get order                |
| GET    | `/api/orders`                  | Get all orders           |
| PUT    | `/api/orders/status?orderId=1` | Update order status      |
| PUT    | `/api/orders/modify?orderId=1` | Add / Remove order items |

---

## 📌 Order Business Rules

* ❌ Cannot modify **CANCELLED** or **CONFIRMED** orders
* ❌ Cannot place order with insufficient stock
* ✅ Stock updates automatically on order creation
* ✅ Order total recalculated on modification
* ✅ All order operations are transactional

---

## 🔐 Exception Handling

Custom exceptions used:

* `ResourceNotFoundException`
* `BadRequestException`
* `BusinessException`

Ensures:

* Meaningful error messages
* Clean API responses
* Proper HTTP status codes

---

## ▶️ Running the Application

### 1️⃣ Clone the repository

```bash
git clone https://github.com/aishwarya882/Order-Management-System.git
cd order-management-system
```

### 2️⃣ Run the application

```bash
mvn spring-boot:run
```

### 3️⃣ Access APIs

```
http://localhost:8080
```

---

## 🧪 Testing with Postman

* Import endpoints manually
* Use JSON request bodies
* All APIs follow REST conventions

---
