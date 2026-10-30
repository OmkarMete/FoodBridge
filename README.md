# FoodBridge – Food Donation Management System

## Overview

FoodBridge is a web-based Food Donation Management System designed to reduce food wastage by connecting food donors with NGOs. It provides a platform where donors can share surplus food information and NGOs can find and accept suitable food donations for distribution to people in need.

## Objectives

- Reduce food wastage by encouraging food donations.
- Connect food donors with NGOs through a common platform.
- Simplify food donation and collection management.
- Provide secure access through authentication and role-based authorization.

## User Roles

### 1. Donor

- Register and log in securely.
- Add surplus food donation details.
- Specify food quantity and availability.
- Manage donation information.

### 2. NGO

- Register and log in securely.
- View available food donations.
- Accept suitable donations.
- Manage food collection and distribution activities.

## Key Features

- User Registration and Login
- Spring Security Authentication
- Role-Based Authorization
- Donor and NGO Management
- Food Donation Management
- Secure Access to User-Specific Features

## Technology Stack

- **Backend:** Java, Spring Boot, Spring MVC
- **Security:** Spring Security
- **Database:** PostgreSQL
- **ORM:** Hibernate / Spring Data JPA
- **Frontend:** JSP, HTML, CSS, Bootstrap
- **Build Tool:** Maven
- **IDE:** Spring Tool Suite (STS)

## Application Workflow

1. Donors and NGOs register on the platform.
2. Users log in through the secure authentication system.
3. Spring Security verifies user credentials.
4. Role-based authorization provides access according to the user's role.
5. Donors manage food donations.
6. NGOs view and accept available donations.
7. Donation information is managed through PostgreSQL.

## Project Architecture

The project follows a layered architecture:

- **Controller Layer:** Handles HTTP requests.
- **Service Layer:** Contains business logic.
- **Repository/DAO Layer:** Handles database operations.
- **Entity Layer:** Represents database entities.
- **Security Layer:** Handles authentication and authorization.
- **View Layer:** Provides the user interface using JSP.

## Application Configuration

The project uses `application.properties` to configure the database, JPA, JSP view resolver, server port, and email service.

### 1. PostgreSQL Configuration

The application connects to a PostgreSQL database named `fddms`.

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/fddms
spring.datasource.username=${DB_USERNAME}
spring.datasource.password=${DB_PASSWORD}
spring.datasource.driver-class-name=org.postgresql.Driver
```

### 2. JPA and Hibernate Configuration

```properties
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.database-platform=org.hibernate.dialect.PostgreSQLDialect
```

- `ddl-auto=update` automatically updates the database schema based on entity changes.
- `show-sql=true` displays SQL queries in the console.
- `format_sql=true` formats SQL queries for readability.
- `PostgreSQLDialect` configures Hibernate to use PostgreSQL-specific SQL.

### 3. JSP Configuration

```properties
spring.mvc.view.prefix=/WEB-INF/views/
spring.mvc.view.suffix=.jsp
```

These properties configure the JSP view location and file extension.

### 4. Server Configuration

```properties
server.port=8080
```

The application runs on port 8080 by default.

### 5. Email Configuration

```properties
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=${MAIL_USERNAME}
spring.mail.password=${MAIL_PASSWORD}
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true
```

This configuration uses Gmail SMTP for email functionality. Credentials are supplied through environment variables instead of being stored directly in the project.

### Important Configuration Changes

For security reasons, sensitive credentials have been replaced with environment variables.

| Previous Configuration | Updated Configuration |
|---|---|
| `spring.datasource.username=postgres` | `${DB_USERNAME}` |
| Actual database password | `${DB_PASSWORD}` |
| Actual Gmail address | `${MAIL_USERNAME}` |
| Actual Gmail App Password | `${MAIL_PASSWORD}` |

This prevents database and email credentials from being exposed in the public GitHub repository.

## Installation and Setup

### Prerequisites

Make sure you have installed:

- Java JDK (compatible with the project's Spring Boot version)
- Spring Tool Suite (STS)
- PostgreSQL
- Maven
- Git

### Step 1: Clone the Repository

Open a terminal and execute:

```bash
git clone https://github.com/YOUR_USERNAME/FoodBridge.git
```

### Step 2: Open the Project in STS

1. Open Spring Tool Suite.
2. Select **File → Import**.
3. Choose **Maven → Existing Maven Projects**.
4. Click **Next**.
5. Browse to the cloned FoodBridge project folder.
6. Select the `pom.xml` file.
7. Click **Finish**.

### Step 3: Create the PostgreSQL Database

Open PostgreSQL or pgAdmin and execute:

```sql
CREATE DATABASE fddms;
```

Make sure PostgreSQL is running on port `5432`.

### Step 4: Configure Environment Variables

The application requires the following environment variables:

| Variable | Description |
|---|---|
| `DB_USERNAME` | PostgreSQL username |
| `DB_PASSWORD` | PostgreSQL password |
| `MAIL_USERNAME` | Gmail account used for SMTP |
| `MAIL_PASSWORD` | Gmail App Password |

In STS:

1. Right-click the project.
2. Select **Run As → Run Configurations**.
3. Select your Spring Boot application.
4. Open the **Environment** tab.
5. Add the required variables with your own credentials.
6. Click **Apply**.

### Step 5: Update Maven Dependencies

1. Right-click the project.
2. Select **Maven → Update Project**.
3. Select your project.
4. Click **OK**.
5. Wait for Maven to download the required dependencies.

### Step 6: Run the Application

1. Right-click the FoodBridge project.
2. Select **Run As → Spring Boot App**.
3. Wait for the application to start.
4. Check the STS console for a successful startup message.

### Step 7: Open the Application

Open your browser and visit:

```text
http://localhost:8080
```

If the application uses a specific controller mapping for its home or login page, open that URL instead.

## Future Enhancements

- Food donation tracking.
- Email notifications for donation requests.
- Donation history and reporting.
- Location-based NGO and donor matching.
- Food expiry and availability notifications.

## Purpose

FoodBridge aims to create a simple and secure digital platform that encourages food donation, reduces food wastage, and helps NGOs distribute surplus food to people in need.
