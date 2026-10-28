# 🍽️ Food Ordering Management System

A **console-based Java Food Ordering Management System** built as a training project to demonstrate practical backend development using **Java, JPA, Hibernate ORM, Maven, and MySQL**.

The application simulates a simple food-ordering workflow where customers can browse restaurants and menu items, manage a shopping cart, place orders, track order status, and view basic sales reports.

> **Project Type:** Console Application  
> **Focus:** Java Backend + JPA/Hibernate + MySQL  
> **Frontend:** Not required  
> **Framework:** No Spring Boot

---

## 📌 Project Description

The **Food Ordering Management System** is designed to demonstrate how a Java backend application can manage real-world business entities and relationships using **Jakarta Persistence API (JPA)** and **Hibernate ORM**.

The system provides a complete basic ordering flow:

**Customer → Restaurant → Menu → Cart → Checkout → Order → Order Status → Reports**

It uses a relational MySQL database for persistent storage and demonstrates entity relationships, CRUD operations, transactions, JPQL queries, validation, and business rules.

This project is suitable for **Java/J2EE backend training, academic submission, GitHub portfolio work, and learning ORM concepts**.

---

## ✨ Features

### 👤 Customer Management
- Create and manage customer records
- Validate customer information
- Search customers
- Maintain customer-specific shopping carts
- View customer order history

### 🏪 Restaurant & Menu Management
- Manage restaurants
- Organize menu items by category
- View restaurant menus
- Search and browse available food items
- Store item names, descriptions, and prices

### 🛒 Shopping Cart
- Add menu items to cart
- Update item quantities
- Remove items from cart
- Calculate cart totals
- Maintain persistent cart data

### 📦 Order Management
- Checkout directly from the cart
- Create orders using database transactions
- Store order items with price/name snapshots
- Store delivery address with the order
- Automatically clear the cart after successful checkout
- Track order status

### 🔄 Order Status
Supported order states include:

- `PLACED`
- `CONFIRMED`
- `PREPARING`
- `OUT_FOR_DELIVERY`
- `DELIVERED`
- `CANCELLED`

The application also validates status transitions according to the defined business rules.

### 📊 Reports
- View order information
- Generate basic sales reports
- Sales calculations consider delivered orders
- JPQL aggregate queries are used for reporting

---

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| **Java 25** | Core application development |
| **Jakarta Persistence API (JPA)** | Persistence and ORM standard |
| **Hibernate ORM 6.6.1** | JPA implementation |
| **MySQL 8.x** | Relational database |
| **MySQL Connector/J 9.1.0** | Java-MySQL connectivity |
| **Maven 3.9+** | Build and dependency management |
| **JUnit 5.11.3** | Unit testing |
| **JPQL** | Database queries and reporting |
| **Git & GitHub** | Version control and project hosting |

---

## 🏗️ Project Architecture

```text
Console UI
    │
    ▼
Service Layer
    │
    ├── CustomerService
    ├── CatalogService
    ├── OrderService
    └── ReportService
    │
    ▼
JPA / EntityManager
    │
    ▼
Hibernate ORM
    │
    ▼
MySQL Database
```

### Main Entities

```text
Customer
   │
   ├── ShoppingCart
   │       └── CartItem
   │
   └── CustomerOrder
           └── OrderItem

Restaurant
   │
   └── MenuItem
           │
           └── Category
```

The project demonstrates:

- `@OneToOne`
- `@OneToMany`
- `@ManyToOne`
- Entity relationships
- Cascade operations
- Database transactions
- EntityManager lifecycle
- JPQL queries
- Validation
- Business-rule enforcement

---

## 📂 Project Structure

```text
food-ordering-system/
│
├── database/
│   └── schema.sql
│
├── docs/
│   ├── DEMO_GUIDE.md
│   ├── ER_DIAGRAM.md
│   └── FEATURES.md
│
├── scripts/
│   └── run.ps1
│
├── src/
│   ├── main/
│   │   ├── java/com/foodordering/
│   │   │   ├── entity/
│   │   │   ├── seed/
│   │   │   ├── service/
│   │   │   ├── util/
│   │   │   └── Main.java
│   │   │
│   │   └── resources/
│   │       └── META-INF/
│   │           └── persistence.xml
│   │
│   └── test/
│       └── java/com/foodordering/
│
├── .env.example
├── .gitignore
├── CONTRIBUTING.md
├── LICENSE
├── pom.xml
└── README.md
```

---

## ⚙️ Prerequisites

Before running the project, install:

1. **JDK 25 or later**
2. **Maven 3.9 or later**
3. **MySQL 8.x**
4. **Git** (optional, for GitHub)

Check your installations:

```bash
java -version
mvn -version
mysql --version
```

---

## 🗄️ Database Setup

Create the database in MySQL:

```sql
CREATE DATABASE food_ordering_db
CHARACTER SET utf8mb4
COLLATE utf8mb4_unicode_ci;
```

You can also use the SQL script provided in:

```text
database/schema.sql
```

---

## 🔐 Environment Configuration

Create a local `.env` file in the project root.

Example:

```dotenv
DB_URL=jdbc:mysql://localhost:3306/food_ordering_db?useSSL=false&serverTimezone=UTC
DB_USER=root
DB_PASSWORD=YOUR_MYSQL_PASSWORD
HIBERNATE_DDL=update
```

### Important

Do **not** commit your real database password to GitHub.

The project includes `.env.example` as a configuration template.

For local development, `HIBERNATE_DDL=update` can be used to allow Hibernate to update the database schema automatically.

---

## ▶️ Running the Project

### Windows PowerShell

From the project root:

```powershell
.\scripts\run.ps1
```

The application can also be run through Maven:

```powershell
mvn clean package
mvn -q exec:java
```

### Linux / macOS

```bash
mvn clean package
mvn test
mvn -q exec:java
```

---

## 🌱 Sample Data

When the database is empty, the application can seed sample data.

The sample dataset contains:

- **3 restaurants**
- **5 categories**
- **11 menu items**
- **3 customers**

Example customers:

```text
aarav@example.com
sneha@example.com
rohan@example.com
```

Generated database IDs may vary.

---

## 🧪 Testing

Run the unit tests with:

```bash
mvn test
```

The test suite covers important business validations such as:

- Required fields
- Customer email validation
- Menu item price validation
- Cart quantity validation
- Order status rules

The project does not currently include automated MySQL integration tests.

---

## 💡 Key Backend Concepts Demonstrated

This project is intentionally focused on backend fundamentals rather than UI development.

### JPA & Hibernate

- Entity mapping
- Persistence context
- `EntityManager`
- Entity relationships
- CRUD operations
- JPQL
- Transaction management

### Database

- Relational database design
- Primary and foreign keys
- Constraints
- Relationships
- Persistent data storage

### Java

- Object-oriented programming
- Classes and enums
- Service-layer architecture
- Exception handling
- Input validation
- `BigDecimal` for monetary values

### Software Development

- Maven dependency management
- Unit testing with JUnit
- Git version control
- Environment-based configuration
- Separation of entities, services, and utilities

---

## 🔒 Transactional Checkout

Checkout is handled as a database transaction.

The basic workflow is:

```text
Validate Cart
     ↓
Calculate Total
     ↓
Create Order
     ↓
Create Order Items
     ↓
Save Order
     ↓
Clear Cart
     ↓
Commit Transaction
```

If an error occurs during checkout, the transaction can be rolled back to prevent partially completed orders.

---

## 📈 Future Improvements

The project can be extended with:

- User authentication and login
- Admin and customer roles
- Password hashing
- REST API using Spring Boot
- Web frontend using React
- Online payment integration
- Delivery fee and tax calculation
- Restaurant owner dashboard
- Inventory management
- Order notifications
- MySQL integration testing
- Docker support
- API documentation using Swagger/OpenAPI

---

## 🎓 Academic / Training Purpose

This project was developed as a **Java backend training project** to demonstrate practical implementation of:

> **Java + JPA + Hibernate + MySQL + Maven**

Instead of using a frontend framework, the application uses a **console-based interface** so that the focus remains on backend logic, database persistence, ORM, transactions, and business rules.

---

## 🚀 GitHub

To publish the project:

```bash
git init
git add .
git commit -m "Initial commit: Food Ordering Management System"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/food-ordering-system.git
git push -u origin main
```

Replace `YOUR_USERNAME` with your GitHub username.

Before pushing, verify that `.env` and other files containing credentials are excluded from Git.

---

## 📄 License

This project is available under the **MIT License**.

See the `LICENSE` file for details.

---

## 👨‍💻 Author

**Aditya Satpute**

Java Backend Development | JPA | Hibernate | MySQL | Maven
