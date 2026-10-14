# Student Records CRUD API

A Node.js + Express + MongoDB + Mongoose REST API for creating, reading, updating, and deleting student records.

## Requirements
- Node.js and npm
- MongoDB Community Server running locally
- VS Code
- Postman (recommended for POST, PATCH, and DELETE requests)

## Run in VS Code
1. Extract/open the `StudentRecordsAPI` folder in VS Code.
2. Open **Terminal → New Terminal**.
3. Install dependencies:
   ```bash
   npm install
   ```
4. Ensure MongoDB is running. The default connection is `mongodb://127.0.0.1:27017/student_records`.
5. Start the API:
   ```bash
   npm run dev
   ```
6. Open http://localhost:3000 in your browser. You should see `Student Records API is running`.

If you don't want to use nodemon, run `npm start` instead.

## Endpoints
| Method | URL | Purpose |
|---|---|---|
| POST | `http://localhost:3000/students` | Create a student |
| GET | `http://localhost:3000/students` | List all students |
| GET | `http://localhost:3000/students/STUDENT_ID` | Get one student |
| PATCH | `http://localhost:3000/students/STUDENT_ID` | Update a student |
| DELETE | `http://localhost:3000/students/STUDENT_ID` | Delete a student |

### Example POST body (Postman → Body → raw → JSON)
```json
{
  "name": "Anita",
  "age": 20,
  "course": "CSE",
  "email": "anita@example.com"
}
```

Age must be between 16 and 100, and email must be unique. Copy the `_id` from the POST response to test GET/PATCH/DELETE for one student.

## Troubleshooting
- `node` or `npm` not recognized: install Node.js LTS, then reopen VS Code.
- `Cannot find package express` or `mongoose`: run `npm install` in this folder.
- MongoDB connection refused: start the MongoDB Server service and retry.
- Port 3000 already in use: set the `PORT` environment variable or change `PORT` in `server.js`.
