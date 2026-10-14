# Student Management REST API (Spring Boot + MySQL)

This project combines the beginner Spring Boot example (`/hello`) and the Student Management CRUD API from the supplied guides.

## Requirements

- JDK 21
- Maven 3.9+ (or a Maven Wrapper generated for the project)
- MySQL 8+
- VS Code with **Extension Pack for Java** and **Spring Boot Extension Pack**
- Postman (recommended for POST, PUT, and DELETE requests)

## 1. Create the database

Start the MySQL server, then run this SQL in MySQL Workbench or the MySQL command line:

```sql
CREATE DATABASE studentdb;
```

## 2. Configure your MySQL credentials

Open `src/main/resources/application.properties`.

The defaults are:
- username: `root`
- password: `change_me`

Replace `change_me` with your local MySQL root password. Alternatively, set environment variables `DB_USERNAME` and `DB_PASSWORD`.

## 3. Open and run in VS Code

1. Extract the ZIP.
2. In VS Code choose **File → Open Folder** and select the `student-api` folder containing `pom.xml`.
3. Open **Terminal → New Terminal**.
4. Confirm Java and Maven are installed:

```bash
java -version
mvn -version
```

5. Start the app:

```bash
mvn spring-boot:run
```

On the first run Maven downloads dependencies, so an internet connection is needed. Keep the terminal open while using the app.

## 4. Test the Hello API

Open this URL in a browser:

`http://localhost:8080/hello`

Expected response:

`Hello Spring Boot Students!`

## 5. Test student CRUD with Postman

Base URL: `http://localhost:8080`

### Get all students
- Method: `GET`
- URL: `http://localhost:8080/students`

### Create a student
- Method: `POST`
- URL: `http://localhost:8080/students`
- Body → raw → JSON:

```json
{
  "name": "Rahul",
  "email": "rahul@gmail.com",
  "department": "CSE"
}
```

### Get one student
- Method: `GET`
- URL: `http://localhost:8080/students/1` (use the ID returned by your POST request)

### Update a student
- Method: `PUT`
- URL: `http://localhost:8080/students/1` (use the actual ID)
- Body → raw → JSON:

```json
{
  "name": "Rahul Kumar",
  "email": "rahulkumar@gmail.com",
  "department": "AIML"
}
```

### Delete a student
- Method: `DELETE`
- URL: `http://localhost:8080/students/1` (use the actual ID)

## API summary

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/hello` | Hello-world API |
| GET | `/students` | List students |
| GET | `/students/{id}` | Read one student |
| POST | `/students` | Add student |
| PUT | `/students/{id}` | Update student |
| DELETE | `/students/{id}` | Delete student |

## Common issues

- **`mvn` is not recognized:** install Apache Maven or use the Maven Wrapper if your generated project includes `mvnw.cmd`.
- **Database connection refused:** make sure MySQL Server is running.
- **Access denied for user:** correct the password in `application.properties`, or set `DB_USERNAME` and `DB_PASSWORD`.
- **Unknown database `studentdb`:** run `CREATE DATABASE studentdb;` first.
- **Port 8080 already in use:** change `server.port=8081` in `application.properties` and use port 8081 in your URLs.

This project uses MySQL/JPA as specified in the beginner practical guide. It does not use MongoDB.
