# Student Records API

## 1. Project Overview

The Student Records API is a RESTful web service developed using Node.js, Express.js, and MongoDB. It allows users to create, retrieve, update, and delete student records through HTTP requests.

The application stores student information in a MongoDB database and uses Mongoose to define the student schema and interact with the database.

## 2. Objectives

- To develop a REST API for managing student records.
- To perform CRUD (Create, Read, Update, Delete) operations.
- To store student information in MongoDB.
- To validate student data using Mongoose.
- To understand REST API development using Express.js.

## 3. Technologies Used

- **Node.js:** JavaScript runtime environment.
- **Express.js:** Framework for building REST APIs.
- **MongoDB:** NoSQL database for storing student records.
- **Mongoose:** Object Data Modeling (ODM) library for MongoDB.
- **Postman:** Tool for testing API endpoints.
- **Visual Studio Code:** Code editor.

## 4. Features

- Add new student records.
- Retrieve all students.
- Retrieve an individual student by ID.
- Update existing student details.
- Delete student records.
- Validate required fields and student age.
- Prevent duplicate email addresses.
- Handle errors and return appropriate HTTP status codes.

## 5. Project Structure

```text
StudentRecordsAPI/
│
├── controllers/
│   └── studentController.js
│
├── models/
│   └── Student.js
│
├── routes/
│   └── studentRoutes.js
│
├── server.js
├── package.json
└── README.md
```

## 6. Student Data Model

Each student record contains the following fields:

| Field | Data Type | Description |
|---|---|---|
| name | String | Student's name |
| age | Number | Student's age (16–100) |
| course | String | Student's course |
| email | String | Unique student email |
| createdAt | Date | Record creation timestamp |
| updatedAt | Date | Last update timestamp |

## 7. Installation and Setup

### Prerequisites

Install the following software:

- Node.js and npm
- MongoDB Community Server
- Visual Studio Code
- Postman (recommended for testing)

### Step 1: Open the project

Extract the ZIP file and open the `StudentRecordsAPI` folder in VS Code.

### Step 2: Install dependencies

Open the VS Code terminal and execute:

```bash
npm install
```

### Step 3: Start MongoDB

Ensure that your MongoDB server is running locally. The application uses this default database connection:

```text
mongodb://127.0.0.1:27017/student_records
```

The database and collection are created when records are first stored.

### Step 4: Start the API server

Run the following command:

```bash
npm run dev
```

Alternatively, use:

```bash
npm start
```

When the application starts successfully, the terminal displays messages indicating that MongoDB is connected and the server is running.

### Step 5: Verify the application

Open the following URL in your browser:

http://localhost:3000

Expected response:

```json
{
  "message": "Student Records API is running"
}
```

## 8. API Endpoints

Base URL: `http://localhost:3000`

| HTTP Method | Endpoint | Description |
|---|---|---|
| POST | `/students` | Create a student |
| GET | `/students` | Retrieve all students |
| GET | `/students/:id` | Retrieve a student by ID |
| PATCH | `/students/:id` | Update a student's details |
| DELETE | `/students/:id` | Delete a student |

## 9. Testing the API Using Postman

### A. Create a Student

- Method: `POST`
- URL: `http://localhost:3000/students`
- Select **Body → raw → JSON**.

Request body:

```json
{
  "name": "Anita",
  "age": 20,
  "course": "CSE",
  "email": "anita@example.com"
}
```

### B. Retrieve All Students

- Method: `GET`
- URL: `http://localhost:3000/students`

This returns all student records stored in the database.

### C. Retrieve a Student by ID

- Method: `GET`
- URL: `http://localhost:3000/students/STUDENT_ID`

Replace `STUDENT_ID` with the actual MongoDB `_id` returned when creating a student.

### D. Update a Student

- Method: `PATCH`
- URL: `http://localhost:3000/students/STUDENT_ID`

Request body:

```json
{
  "course": "Information Technology"
}
```

### E. Delete a Student

- Method: `DELETE`
- URL: `http://localhost:3000/students/STUDENT_ID`

Replace `STUDENT_ID` with the student's actual ID.

## 10. HTTP Status Codes

- `200 OK`: Request completed successfully.
- `201 Created`: Student record created successfully.
- `400 Bad Request`: Invalid input, student ID, or validation error.
- `404 Not Found`: Student record does not exist.
- `500 Internal Server Error`: Failed to retrieve student records.

## 11. Error Handling and Validation

The application uses `try...catch` blocks to handle errors during database operations.

Mongoose validation ensures that the student's name, age, course, and email are provided. The age must be between 16 and 100, and email addresses must be unique.

## 12. Advantages

- Simple and organized API structure.
- Efficient management of student records.
- Persistent storage using MongoDB.
- Easy integration with web or mobile frontends.
- Supports testing through Postman or other HTTP clients.

## 13. Future Enhancements

- User authentication and authorization.
- Search and filtering of student records.
- Pagination for large datasets.
- Improved email format validation.
- API documentation using Swagger.
- Frontend dashboard for student management.

## 14. Conclusion

The Student Records API demonstrates how to build a RESTful application using Node.js, Express.js, MongoDB, and Mongoose. It provides the essential CRUD operations required to manage student information and serves as a foundation for developing larger student management applications.

## 15. Author

**Project Name:** Student Records API  
**Project Type:** REST API / Backend Development  
**Development Environment:** Visual Studio Code

