# Bank Management System

A robust, console-based banking application built with **Java** and **JDBC**. This system simulates core banking operations with a strong focus on data integrity, security, and transaction management.

## 📌 Overview

This project is a backend simulation of a banking environment. It moves beyond simple CRUD operations by implementing **ACID properties** (Atomicity, Consistency, Isolation, Durability) to ensure financial transactions (like transfers) are safe and reliable. It also features a dual-layer security model to protect user accounts.

<img width="1767" height="709" alt="Banking System1" src="https://github.com/user-attachments/assets/48ec3bba-c2aa-4973-b7d0-a22c043295c6" />
<img width="1681" height="856" alt="Banking System" src="https://github.com/user-attachments/assets/9a957c1b-284c-4d3d-bc3e-9389de7e82c6" />



## 🚀 Key Features

* **Secure Authentication:** User registration and login system using email and password.
* **Dual-Factor Security:** Critical operations (Debit, Credit, Transfer) require a secondary **Security PIN** validation.
* **ACID-Compliant Transactions:** Implements manual **Commit and Rollback** logic. If a money transfer fails halfway (e.g., debit succeeds but credit fails), the system rolls back to the previous state to prevent data inconsistency.
* **SQL Injection Protection:** Uses `PreparedStatement` for all database queries to prevent SQL injection attacks.
* **Account Management:** Automatic account number generation and duplicate verification.

## 🛠️ Tech Stack

* **Language:** Java (JDK 8+)
* **Database:** MySQL
* **Connectivity:** JDBC (Java Database Connectivity)
* **Tools:** Maven/Gradle (optional), IntelliJ IDEA/Eclipse, Git

## ⚙️ Database Setup

To run this project, you must set up the MySQL database. Run the following SQL commands in your MySQL Workbench or Command Line:

```sql
CREATE DATABASE banking_system;

USE banking_system;

-- Table for User Credentials
CREATE TABLE user (
    full_name VARCHAR(255) NOT NULL,
    email VARCHAR(255) PRIMARY KEY,
    password VARCHAR(255) NOT NULL
);

-- Table for Banking Accounts
CREATE TABLE accounts (
    account_number BIGINT PRIMARY KEY,
    full_name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    balance DECIMAL(10,2) NOT NULL,
    security_pin CHAR(4) NOT NULL,
    FOREIGN KEY (email) REFERENCES user(email)
);
