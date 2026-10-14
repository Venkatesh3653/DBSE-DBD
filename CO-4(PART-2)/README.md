# Student Records Management System

## 1. Project Overview

The Student Records Management System is a backend REST API developed using Java, Spring Boot, and MongoDB. It enables users to register and log in securely and manage student records through HTTP requests.

The application implements CRUD operations (Create, Read, Update, and Delete) and uses JSON Web Tokens (JWT) to authenticate users before allowing access to student management endpoints.

## 2. Objectives

- Develop a RESTful API using Spring Boot.
- Store student records in MongoDB.
- Implement user registration and login.
- Secure API endpoints using JWT authentication.
- Perform CRUD operations on student records.
- Validate input data and handle errors appropriately.

## 3. Technologies Used

- **Programming Language:** Java 17
- **Backend Framework:** Spring Boot 3.5.6
- **Database:** MongoDB
- **Database Integration:** Spring Data MongoDB
- **Security:** Spring Security
- **Authentication:** JSON Web Token (JWT)
- **Build Tool:** Apache Maven
- **API Testing:** Postman
- **IDE:** Visual Studio Code

## 4. Features

- User registration and login.
- Password hashing for secure storage.
- JWT token generation and authentication.
- Create new student records.
- Retrieve all student records.
- Retrieve a student by ID.
- Update existing student details.
- Delete student records.
- Request validation and centralized exception handling.

## 5. Project Structure

```text
student-records/
├── src/
│   └── main/
│       ├── java/com/example/studentrecords/
│       │   ├── StudentRecordsApplication.java
│       │   ├── controller/
│       │   │   ├── AuthController.java
│       │   │   └── StudentController.java
│       │   ├── dto/
│       │   │   ├── LoginRequest.java
│       │   │   ├── RegisterRequest.java
│       │   │   └── StudentRequest.java
│       │   ├── entity/
│       │   │   ├── Student.java
│       │   │   └── User.java
│       │   ├── exception/
│       │   │   └── GlobalExceptionHandler.java
│       │   ├── repository/
│       │   │   ├── StudentRepository.java
│       │   │   └── UserRepository.java
│       │   ├── security/
│       │   │   ├── CustomUserDetailsService.java
│       │   │   ├── JwtAuthFilter.java
│       │   │   ├── JwtUtil.java
│       │   │   └── SecurityConfig.java
│       │   └── service/
│       │       └── StudentService.java
│       └── resources/
│           └── application.properties
├── pom.xml
├── run-project.bat
└── README.md
```

## 6. Prerequisites

Install the following before running the application:

1. Java Development Kit (JDK) 17 or later.
2. MongoDB Community Server.
3. Apache Maven.
4. Visual Studio Code.
5. Postman for API testing.

Verify Java and Maven installations:

```bash
java -version
javac -version
mvn -version
```

## 7. Installation and Setup

### Step 1: Extract the project

Extract the ZIP file and open the `student-records` folder in Visual Studio Code. Make sure the folder contains `pom.xml`.

### Step 2: Start MongoDB

Start the MongoDB Community Server on your computer.

The application connects to:

```text
mongodb://localhost:27017/student_records
```

### Step 3: Run the application

Open the VS Code terminal inside the project folder and execute:

```bash
mvn spring-boot:run
```

Alternatively, on Windows, double-click `run-project.bat` or run it from the terminal.

Wait until Spring Boot starts successfully on port `8080`.

### Step 4: Test the API

Use Postman to send requests to:

```text
http://localhost:8080
```

This project is a backend REST API. It does not provide a graphical frontend by default.

## 8. API Endpoints

Base URL: `http://localhost:8080`

| HTTP Method | Endpoint | Description |
|---|---|---|
| POST | `/auth/register` | Register a user |
| POST | `/auth/login` | Log in and receive a JWT |
| POST | `/students` | Create a student |
| GET | `/students` | Retrieve all students |
| GET | `/students/{id}` | Retrieve a student by ID |
| PUT | `/students/{id}` | Update a student |
| DELETE | `/students/{id}` | Delete a student |

**Authentication:** The student endpoints require a valid JWT Bearer token.

## 9. Testing with Postman

### A. Register a user

- Method: `POST`
- URL: `http://localhost:8080/auth/register`
- Body → raw → JSON

```json
{
  "username": "asha",
  "password": "secret123"
}
```

### B. Log in

- Method: `POST`
- URL: `http://localhost:8080/auth/login`
- Body → raw → JSON

```json
{
  "username": "asha",
  "password": "secret123"
}
```

Copy the JWT token returned in the response.

### C. Create a student

- Method: `POST`
- URL: `http://localhost:8080/students`

Under Authorization, select **Bearer Token** and paste the token received during login.

Request body:

```json
{
  "name": "Asha Rao",
  "age": 20,
  "course": "B.Tech CSE",
  "email": "asha@example.com"
}
```

### D. Retrieve all students

- Method: `GET`
- URL: `http://localhost:8080/students`

Include the Bearer token in the Authorization tab.

### E. Retrieve a student by ID

- Method: `GET`
- URL: `http://localhost:8080/students/{id}`

Replace `{id}` with the actual MongoDB ID of the student.

### F. Update a student

- Method: `PUT`
- URL: `http://localhost:8080/students/{id}`

Provide the Bearer token and the updated student information in the JSON request body.

### G. Delete a student

- Method: `DELETE`
- URL: `http://localhost:8080/students/{id}`

Provide the Bearer token and replace `{id}` with the student's actual ID.

## 10. Database

The application uses MongoDB to persist user and student information.

- **Database name:** `student_records`
- **User
