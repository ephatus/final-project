

# 📘 SME Financial Management Database

## 📌 Project Overview

This project implements a **relational database system** for managing SME (Small and Medium Enterprise) financial data.
The database is designed to support **transactions, products, customers, vendors, and AI-driven risk assessments**, forming the backbone for future **FinTech analytics and dashboards**.

It demonstrates **SQL fundamentals** including:

* Structured schema design
* Primary and foreign key relationships
* Constraints (NOT NULL, UNIQUE, ENUM)
* Normalized tables for real-world financial management

---

## 🎯 Objectives

* Build a **complete database management system** using MySQL.
* Model real-world financial workflows for SMEs.
* Enable integration with **Python ML modules** for risk analysis.
* Provide a foundation for **dashboards and reporting tools**.

---

## 🛠️ Tech Stack

* **Database Engine:** MySQL
* **Query Language:** SQL
* **Optional Integrations:** Python (Pandas, SQLAlchemy)

---

## 📂 Database Schema

### Tables:

1. **Customers** → stores SME clients
2. **Products** → catalog of goods/services
3. **Vendors** → suppliers and service providers
4. **Transactions** → sales/purchase records linked to customers, vendors & products
5. **Risk_Assessment** → ML-driven risk predictions (Low/Medium/High)

---

## 🔗 Entity-Relationship Diagram (ERD)

```
Customers ───< Transactions >─── Products
                 │
                 v
              Vendors
                 │
                 v
         Risk_Assessment
```

---

## 📜 Example SQL Implementation

```sql
-- Create Database
CREATE DATABASE sme_financial_db;
USE sme_financial_db;

-- Customers Table
CREATE TABLE Customers (
    customer_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    phone VARCHAR(20),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Products Table
CREATE TABLE Products (
    product_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    category VARCHAR(50),
    unit_price DECIMAL(10,2) NOT NULL
);

-- Vendors Table
CREATE TABLE Vendors (
    vendor_id INT AUTO_INCREMENT PRIMARY KEY,
    vendor_name VARCHAR(100) NOT NULL,
    contact_email VARCHAR(100)
);

-- Transactions Table
CREATE TABLE Transactions (
    transaction_id INT AUTO_INCREMENT PRIMARY KEY,
    customer_id INT,
    product_id INT,
    vendor_id INT,
    date DATE NOT NULL,
    quantity INT NOT NULL,
    revenue DECIMAL(10,2) NOT NULL,
    expense DECIMAL(10,2),
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id),
    FOREIGN KEY (product_id) REFERENCES Products(product_id),
    FOREIGN KEY (vendor_id) REFERENCES Vendors(vendor_id)
);

-- Risk Assessment Table
CREATE TABLE Risk_Assessment (
    assessment_id INT AUTO_INCREMENT PRIMARY KEY,
    transaction_id INT NOT NULL,
    risk_level ENUM('Low', 'Medium', 'High') NOT NULL,
    notes TEXT,
    FOREIGN KEY (transaction_id) REFERENCES Transactions(transaction_id)
);
```

---

## 🚀 Getting Started

1. Clone this repository:

   ```bash
   git clone https://github.com/your-username/sme-financial-db.git
   cd sme-financial-db
   ```

2. Import the schema into MySQL:

   ```bash
   mysql -u root -p < sme_financial_db.sql
   ```

3. Verify tables:

   ```sql
   USE sme_financial_db;
   SHOW TABLES;
   ```

---

## 📊 Sample Use Cases

* Insert transaction data from **CSV or Python script**.
* Query top customers, best-selling products, or vendors.
* Store **AI-generated risk predictions** in `Risk_Assessment`.
* Connect with **Streamlit/Dash dashboards** for visualization.

---

## 🌟 Impact

This database forms the foundation for **AI-powered risk management in SMEs**, enabling:

* Smarter financial planning
* Easier integration with ML models
* Scalable FinTech solutions

---

