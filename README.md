# 🛒 Order Management System
 
A RESTful backend service for creating, retrieving, updating, and canceling customer orders — built with **Spring Boot**, **PostgreSQL**, and **JPA/Hibernate**. Supports multi-item orders, billing details, and bulk operations
 
 
---
 
 
## 🔍 Overview
 
This project is a microservice-style API for managing customer orders. Each order can contain multiple line items and is linked to a billing address, backed by a real relational database rather than in-memory storage - making it a closer approximation of a production-grade order system.
 
Key design goals:
- **Clean layering** — Controller → Service → Repository
- **Decoupled contracts** — request/response DTOs are kept separate from JPA entities
---
 
## 🛠 Tech Stack
 
| Layer | Technology |
|---|---|
| Language | Java  |
| Framework | Spring Boot (Spring Web, Spring Data JPA) |
| Database | PostgreSQL |
| ORM | Hibernate |
| Build Tool | Maven (with Maven Wrapper) |
 
---
 
## 🗃 Data Model
 
```
Order (1) ──── (1) Billing
  │
  └──── (*) OrderItem
```
 
- **Order** — status, subtotal, tax, total, shipping charge, customer ID, creation timestamp
- **OrderItem** — item name, quantity (many per order)
- **Billing** — address line 1/2, city, state, zip code (one per order)
---
 
## 🚀 Getting Started
 
### Prerequisites
- Java 8+
- Maven (or use the included wrapper `./mvnw`)
- PostgreSQL running locally (or via Docker)
### 1. Clone the repository
```bash
git clone  https://github.com/Smitbhuva15/Order-Management-System.git
cd Order-Management-System
```
 
### 2. Configure the database
Update `src/main/resources/application.properties` with your PostgreSQL credentials:
```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/postgres
spring.datasource.username=postgres
spring.datasource.password=yourpassword
```
 
> ⚠️ For local development only — never commit real credentials. Consider externalizing these via environment variables for production use.
 
### 3. Build and run
```bash
./mvnw clean install
./mvnw spring-boot:run
```
 
The app starts on **`http://localhost:8080`**.
 

 
---
 
## 📡 API Reference
 
Base path: `/api/v1/order`
 
| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/create` | Create a single order with items + billing |
| `POST` | `/create/bulk` | Create multiple orders in one request |
| `GET` | `/{id}` | Retrieve an order by ID |
| `PUT` | `/update/{id}` | Update an existing order |
| `PUT` | `/update/bulk/{id}` | Update multiple orders |
| `DELETE` | `/cancel/{id}` | Cancel (delete) an order |
 

 
## 📁 Project Structure
 
```
src/main/java/com/egen/
├── controller/     # REST endpoints
├── entity/         # JPA entities (Order, OrderItem, Billing)
├── exceptions/      # Custom exceptions + error response model
├── repository/      # Spring Data JPA repositories
├── service/         # Business logic (interface + implementation)
└── vo/               # Request/response DTOs
```
 
---

 

<br />

<div align="center">
  <h3>Designed &  Developed By ❤️ Smit Bhuva</h3>
</div>