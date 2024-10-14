# H2 Database Demo

This project demonstrates how to integrate an H2 in-memory database into a Spring Boot application. It covers:

- Understanding the H2 database
- Using `schema.sql` and `data.sql` files
- Running the project
- Accessing the H2 console

## Table of Contents
- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Project Structure](#project-structure)
- [Understanding H2 Database](#understanding-h2-database)
- [Using schema.sql and data.sql](#using-schemasql-and-datasql)
- [Running the Project](#running-the-project)
- [Accessing the H2 Console](#accessing-the-h2-console)
- [Troubleshooting](#troubleshooting)

## Introduction

This application is a simple Spring Boot project that uses an H2 in-memory database. It demonstrates how to configure the database, initialize it with SQL scripts, and interact with it using the H2 console.

## Prerequisites

- Java 17 or higher
- Gradle build tool
- An IDE like IntelliJ IDEA or Eclipse (optional)

## Project Structure

```bash
src
└── main
    ├── java
    │   └── com.example.h2databasedemo
    │       └── H2DatabaseDemoApplication.java
    └── resources
        ├── application.properties
        ├── schema.sql
        └── data.sql
```
## Understanding H2 Database

H2 is an open-source relational database management system written in Java. It can be embedded in Java applications or run in client-server mode. In this project, we use H2 in embedded mode:

- **In-Memory Database**: Data is stored in memory, which means it's fast but not persistent after the application stops.
- **Embedded Mode**: Runs within the same JVM as the application, simplifying development and testing.
- **H2 Console**: A web-based interface to interact with the database.

## Using schema.sql and data.sql

Spring Boot automatically runs `schema.sql` and `data.sql` files on startup to initialize the database.

- **schema.sql**: Contains SQL statements to create tables and define the database schema.
- **data.sql**: Contains SQL statements to insert initial data into the tables.

### Example `schema.sql`

```sql
CREATE TABLE users (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255)
);
```
### Example `schema.sql`
```sql
INSERT INTO users (name) VALUES ('John Doe');
INSERT INTO users (name) VALUES ('Jane Smith');
```
Place these files in the src/main/resources directory.

## Running the Project
### Clone the Repository
```bash
git clone https://github.com/your-username/h2-database-demo.git
cd h2-database-demo
```
### Build the Project
```bash
./gradlew build
```
### Run the Application
```bash
./gradlew bootRun
```
Alternatively, run the H2DatabaseDemoApplication class from your IDE.

## Accessing the H2 Console

### Open Browser

Navigate to `http://localhost:8080/h2-console`.

### Configure Connection

- **JDBC URL**: `jdbc:h2:mem:testdb`
- **User Name**: `sa`
- **Password**: Use the password set in `application.properties`.

### Connect

Click the "Connect" button to access the database.

## Troubleshooting

- **Cannot Access H2 Console**: Ensure `spring.h2.console.enabled=true` is set in `application.properties`.
- **Database Not Found Error**: Verify the JDBC URL and that the application is running.
- **SQL Syntax Errors**: Check for typos in `schema.sql` and `data.sql`.
