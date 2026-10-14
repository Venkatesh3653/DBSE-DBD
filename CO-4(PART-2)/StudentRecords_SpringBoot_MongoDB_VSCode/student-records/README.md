# Student Records Application — Spring Boot + MongoDB

This project follows the two supplied guides. It provides student CRUD endpoints, registration/login, password hashing, JWT authentication, and request validation.

## Requirements
- JDK 17 (verify with `java -version` and `javac -version`)
- MongoDB Community Server running at `mongodb://localhost:27017`
- Apache Maven installed (`mvn -version`)
- VS Code with the Extension Pack for Java (Spring Boot Extension Pack is recommended)
- Postman for testing POST/PUT/DELETE and authentication requests

## Run in VS Code (Windows)
1. Extract the ZIP.
2. In VS Code, choose **File → Open Folder** and select this `student-records` folder — the folder containing `pom.xml`.
3. Open **Terminal → New Terminal**.
4. Make sure MongoDB Community Server is running.
5. Run:
   ```powershell
   mvn spring-boot:run
   ```
6. Wait until Spring Boot starts on port 8080.

If `mvn` is not recognized, install/configure Apache Maven or use the Maven Wrapper if you generate one for this project. If MongoDB connection fails, start the MongoDB Windows service and run again.

## Endpoints
- `POST http://localhost:8080/auth/register`
- `POST http://localhost:8080/auth/login`
- `POST http://localhost:8080/students` (Bearer token required)
- `GET http://localhost:8080/students` (Bearer token required)
- `GET http://localhost:8080/students/{id}` (Bearer token required)
- `PUT http://localhost:8080/students/{id}` (Bearer token required)
- `DELETE http://localhost:8080/students/{id}` (Bearer token required)

## Register in Postman
Method: POST  
URL: `http://localhost:8080/auth/register`  
Body → raw → JSON:
```json
{"username":"asha","password":"secret123"}
```

## Login in Postman
Method: POST  
URL: `http://localhost:8080/auth/login`  
Body → raw → JSON:
```json
{"username":"asha","password":"secret123"}
```
Copy the `token` returned by login. For every `/students` request, choose Authorization → Bearer Token and paste it.

## Create a student
Method: POST  
URL: `http://localhost:8080/students`  
Authorization: Bearer Token  
Body → raw → JSON:
```json
{"name":"Asha Rao","age":20,"course":"B.Tech CSE","email":"asha@example.com"}
```

The API is a backend REST API, not a browser-based graphical website. Use Postman to test JSON requests. Data is saved in MongoDB database `student_records`.
