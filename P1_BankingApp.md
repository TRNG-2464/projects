# Project Instructions

## Project Overview

You will build a console-based banking application using Java. The application will allow customers to register, manage bank accounts, deposit and withdraw money, transfer money between accounts, and review their transaction history.

Your application must support two database options:

- PostgreSQL
- MongoDB

You will use the DAO design pattern to separate the application’s business logic from its database logic. PostgreSQL and MongoDB must each have their own DAO implementations, but both implementations must follow the same DAO interfaces.

The application must select the appropriate database implementation through configuration. Changing from PostgreSQL to MongoDB should not require changes to the console menus, service classes, or banking business logic.

This is a backend-focused project. All user interaction will take place through a command-line or console interface.

## Tools and Technologies Used

Required technologies:
- Java
- Maven
- PostgreSQL
- JDBC
- MongoDB
- MongoDB Java Driver
- Git
- GitHub
- JUnit

## Required concepts:
- Object-oriented programming
- Interfaces and abstraction
- Encapsulation
- Collections
- Exception handling
- Input validation
- Layered application architecture
- DAO design pattern
- CRUD operations
- SQL queries
- NoSQL document operations
- Configuration-based database selection
- Unit testing

## Suggested Architecture

Your application should contain the following layers.

### Presentation Layer
- The presentation layer manages all console-based interaction with the user.

Responsibilities include:
- Displaying menus and available actions
- Reading and validating console input
- Displaying results and error messages
- Sending user requests to the service layer
- Avoiding direct database access and business logic

### Service Layer
- The service layer contains the banking rules and application workflows.

Responsibilities include:
- Processing customer registration and authentication
- Managing customer and account operations
- Processing deposits, withdrawals, and transfers
- Validating account ownership and account status
- Coordinating multiple data access operations
- Enforcing banking and transaction rules
- Creating and retrieving transaction records

### Data Access Layer
- The data access layer handles communication with PostgreSQL and MongoDB.

Responsibilities include:
- Defining common DAO interfaces
- Implementing the DAO interfaces for PostgreSQL
- Implementing the DAO interfaces for MongoDB
- Performing create, read, update, and delete operations
- Mapping database records or documents to Java objects
- Handling database-specific errors and connection logic
- Supporting the same required features for both database implementations

### Model Layer
The model layer represents the application’s core business data.

Responsibilities include:
- Defining customers, bank accounts, and transactions
- Storing the fields and relationships required by the application
- Encapsulating model data
- Supporting consistent use of data across the service and DAO layers

Configuration Layer
- The configuration layer determines which database implementation the application uses.

Responsibilities include:
- Reading the selected database type from configuration
- Providing the appropriate PostgreSQL or MongoDB DAO implementations
- Managing database connection settings
- Keeping credentials and connection values outside the source code
- Allowing the database implementation to change without modifying business logic

Instructions
1. Set Up the Project

Create a Maven-based Java application

Initialize a Git repository and commit project changes regularly throughout development (you should have a commit history showing multiple commits)

2. Create the Application Models

At minimum, the application should include models for:

Customers
Bank accounts
Transactions

3. Design the PostgreSQL Database

Design a relational database that stores customer, account, and transaction information.

4. Design the MongoDB Database

Design a MongoDB database that supports the same banking features as the PostgreSQL database.

Create the necessary collections and determine how related data will be stored using embedded documents or references.


5. Define the DAO Interfaces
Create DAO interfaces that define the database operations required by the service layer.

The interfaces should support the customer, account, and transaction operations described in the user stories and project checklist.

The same DAO interfaces must be used by both PostgreSQL and MongoDB implementations.

6. Implement Data Access for PostgreSQL and MongoDB

Implement the DAO interfaces for PostgreSQL with JDBC and MongoDB using MongoDB Java Driver.

7. Implement Configurable Database Selection

Create a configuration mechanism that allows the application to use either PostgreSQL or MongoDB.

The selected database should be controlled through a configuration value rather than by changing the service or presentation code.

8. Implement the Banking Services

Create service-layer logic that supports all required customer, account, and transaction operations.

The service layer should enforce validation, account ownership, account status, balance requirements, and transaction rules.

9. Create the Console Interface

Create a clear console interface that allows users to register, log in, manage accounts, perform transactions, and view transaction history.

The interface should provide understandable menus, prompts, results, and error messages.

10. Add Validation and Exception Handling

Validate all user input and business operations.

The application should handle invalid input, missing records, duplicate data, unauthorized actions, insufficient balances, invalid transactions, and database errors without unexpectedly terminating.

11. Test the Application

Create unit tests for the most important service-layer and banking rules.

Tests should verify successful operations as well as invalid or rejected operations.

The service layer should be testable without requiring a live production database.

12. Document the Project

Create a README.md that explains:

The application purpose
Features
Technologies used
Project architecture
Database designs
Configuration process
Setup and run instructions
Test instructions
DAO implementation
Database selection process
Known limitations
Optional enhancements completed

Do not commit passwords, credentials, or private database connection values to the repository.

## User Stories
### Customer Registration and Authentication

US-01: As a new customer, I want to register for an account so that I can access the banking application.

US-02: As a registered customer, I want to log in securely so that I can access my bank accounts.

US-03: As a customer, I want to update my profile information so that my account details remain accurate.

US-04: As a customer, I want my password or PIN to be stored securely so that my credentials are protected.

### Bank Account Management

US-05: As a customer, I want to open a checking account so that I can manage everyday transactions.

US-06: As a customer, I want to open a savings account so that I can store money separately.

US-07: As a customer, I want to view all of my accounts so that I can understand my banking relationship.

US-08: As a customer, I want to view the balance of an account so that I know how much money is available.

US-09: As a customer, I want to close an eligible account so that I can remove an account I no longer need.

### Deposits and Withdrawals

US-10: As a customer, I want to deposit money into an account so that I can increase its balance.

US-11: As a customer, I want to withdraw money from an account so that I can access my funds.

US-12: As a customer, I want the application to prevent overdrafts so that my account balance does not become invalid.

### Transfers

US-13: As a customer, I want to transfer money between my accounts so that I can organize my funds.

US-14: As a customer, I want to transfer money to another valid account so that I can send funds to another customer.

US-15: As a customer, I want a transfer to complete as one operation so that money is not removed unless it is also deposited successfully.

### Transaction History

US-16: As a customer, I want to view my transaction history so that I can review activity on my account.

US-17: As a customer, I want to filter transactions by type or date so that I can locate specific activity.

US-18: As a customer, I want each transaction to show its amount, date, type, and resulting balance so that I can understand its effect.

### Database Selection

US-19: As a developer, I want the application to use DAO interfaces so that the business logic is not tied to one database.

US-20: As a developer, I want to select PostgreSQL or MongoDB through configuration so that I can change persistence technologies without rewriting the application.

US-21: As a developer, I want both database implementations to support the same core banking features so that application behavior remains consistent.

### Reliability and Validation

US-22: As a customer, I want clear error messages when an operation fails so that I understand how to correct the problem.

US-23: As a bank stakeholder, I want invalid and unauthorized transactions to be rejected so that customer accounts remain protected.

US-24: As a developer, I want important business rules covered by tests so that changes do not introduce unexpected defects.

## Project Requirements Checklist
- Project is built as a Java Maven application and follows a clean, organized package structure with appropriate separation of concerns.
- Application implements appropriate object-oriented design using well-defined model classes and follows the layered architecture (Presentation, Service, Data Access, and Configuration).
- Application includes complete PostgreSQL and MongoDB implementations, with database selection performed through a configurable DAO pattern.
- Application implements all user stories while enforcing appropriate business rules, validation, and exception handling.
- Application uses secure and appropriate database practices, including prepared statements (PostgreSQL), proper resource management, and externalized configuration values.
- Console interface provides a clear, intuitive user experience with appropriate navigation, input validation, and user-friendly error messages.
- Application demonstrates clean, maintainable, and well-documented code that follows established Java coding standards and best practices.
- Application includes a comprehensive suite of automated tests covering the application's business logic and critical functionality.
- Project includes a complete README with setup instructions, architecture overview, database configuration, and execution steps.
- Project is maintained in a Git repository with meaningful commit history demonstrating consistent development throughout the project.