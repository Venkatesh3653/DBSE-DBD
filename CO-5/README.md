# Student Management REST API (Spring Boot + MySQL)

## 1. Project Overview

The Student Management REST API is a backend application developed using Java and Spring Boot. It uses MySQL as its relational database to store and manage student information.

The application provides REST endpoints to create, retrieve, update, and delete student records. It also includes a simple Hello World API to demonstrate the working of Spring Boot.

## 2. Objectives

- Develop a RESTful API using Spring Boot.
- Connect a Java application to a MySQL database.
- Perform CRUD (Create, Read, Update, Delete) operations.
- Store and retrieve student information.
- Understand REST API development and HTTP methods.
- Test API endpoints using Postman.

## 3. Technologies Used

- **Programming Language:** Java 21
- **Framework:** Spring Boot 3.5.6
- **Database:** MySQL 8+
- **ORM:** Spring Data JPA and Hibernate
- **Build Tool:** Apache Maven
- **API Testing:** Postman
- **IDE:** Visual Studio Code

## 4. Features

- Add new student records.
- Retrieve all students.
- Search for a student by ID.
- Update student information.
- Delete student records.
- Automatically generate student IDs.
- Connect and persist data using MySQL.
- Provide a basic Hello World endpoint.

## 5. Project Structure

```text
student-api/
├── src/
│   └── main/
│       ├── java/com/example/studentapi/
│       │   ├── StudentApiApplication.java
│       │   ├── controller/
│       │   │   ├── HelloController.java
│       │   │   └── StudentController.java
│       │   ├── entity/
│       │   │   └── Student.java
│       │   ├── repository/
│       │   │   └── StudentRepository.java
│       │   └── service/
│       │       └── StudentService.java
│       └── resources/
│           └── application.properties
├── pom.xml
└── README.md
```

## 6. Prerequisites

Install the following software:

1. JDK 21.
2. MySQL Server.
3. Apache Maven.
4. Visual Studio Code.
5. Postman (recommended).

Verify the Java and Maven installations:

```bash
java -version
mvn -version
```

## 7. Installation and Setup

### Step 1: Extract the project

Extract the downloaded ZIP file and open the `student-api` folder in VS Code.

Select **File → Open Folder** and choose the folder containing `pom.xml`.

### Step 2: Create the MySQL database

Start MySQL Server and open MySQL Workbench or the MySQL command-line client.

Execute:

```sql
CREATE DATABASE studentdb;
```

### Step 3: Configure database credentials

Open:

`src/main/resources/application.properties`

The default configuration is:

```properties
spring.application.name=student-api

spring.datasource.url=jdbc:mysql://localhost:3306/studentdb
spring.datasource.username=${DB_USERNAME:root}
spring.datasource.password=${DB_PASSWORD:change_me}
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true

server.port=8080
```

Replace `change_me` with your actual MySQL password, or configure the `DB_USERNAME` and `DB_PASSWORD` environment variables.

### Step 4: Run the application

Open the VS Code terminal in the `student-api` folder and execute:

```bash
mvn spring-boot:run
```

Maven downloads the required dependencies on the first run. Wait until the Spring Boot application starts successfully.

### Step 5: Verify the application

Open the following URL in your browser:

http://localhost:8080/hello

Expected response:

```text
Hello Spring Boot Students!
```

## 8. API Endpoints

Base URL: `http://localhost:8080`

| HTTP Method | Endpoint | Description |
|---|---|---|
| GET | `/hello` | Display a welcome message |
| GET | `/students` | Retrieve all students |
| GET | `/students/{id}` | Retrieve a student by ID |
| POST | `/students` | Create a student |
| PUT | `/students/{id}` | Update a student |
| DELETE | `/students/{id}` | Delete a student |

## 9. Testing Using Postman

### A. Create a student

- Method: `POST`
- URL: `http://localhost:8080/students`
- Select **Body → raw → JSON**.

Request body:

```json
{
  "name": "Rahul",
  "email": "rahul@gmail.com",
  "department": "CSE"
}
```

Expected status: `201 Created`

### B. Retrieve all students

- Method: `GET`
- URL: `http://localhost:8080/students`

This returns all student records stored in the database.

### C. Retrieve a student by ID

- Method: `GET`
- URL: `http://localhost:8080/students/1`

Replace `1` with an existing student ID.

### D. Update a student

- Method: `PUT`
- URL: `http://localhost:8080/students/1`

Request body:

```json
{
  "name": "Rahul Kumar",
  "email": "rahulkumar@gmail.com",
  "department": "AIML"
}
```

### E. Delete a student

- Method: `DELETE`
- URL: `http://localhost:8080/students/1`

Replace `1` with the ID of the student you want to delete.

## 10. Database Design

**Database name:** `studentdb`

The Student entity contains the following fields:

| Field | Data Type | Description |
|---|---|---|
| id | Long | Automatically generated primary key |
| name | String | Student's name |
| email | String | Student's email address |
| department | String | Student's department |

Spring Data JPA and Hibernate manage database operations. The configuration `spring.jpa.hibernate.ddl-auto=update` allows Hibernate to update the schema automatically.

## 11. Error Handling

The application handles requests for student records that do not exist by returning `404 Not Found`.

Common errors include:

- **Database connection refused:** Ensure MySQL Server is running.
- **Access denied:** Verify the MySQL username and password.
- **Unknown database:** Create the `studentdb` database.
- **Port already in use:** Change `server.port` in `application.properties`.
- **Maven command not found:** Install Maven and configure its PATH.

## 12. Advantages

- Easy management of student records.
- Reliable relational database storage.
- Organized backend architecture.
- Automatic ID generation.
- Easy integration with frontend applications.
- Standard REST API endpoints for external clients.

## 13. Future Enhancements

- Add student search and filtering.
- Implement input validation.
- Add authentication and authorization.
- Develop a React or HTML/CSS/JavaScript frontend.
- Implement pagination.
- Generate student reports.

## 14. Conclusion

The Student Management REST API demonstrates how to develop a backend application using Java, Spring Boot, Spring Data JPA, and MySQL. It implements the essential CRUD operations required to manage student records and provides a foundation for building a complete student management system.

## 15. Author

**Project Name:** Student Management REST API  
**Framework:** Spring Boot  
**Database:** MySQL  
**Development Environment:** Visual Studio Code

